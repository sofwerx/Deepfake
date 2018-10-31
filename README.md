# Deepfake


INSTRUCTIONS:

Inside the Obamanet folder choose an audio (ie. sagan.wav)

run: python run.py --sf data/audios/sagan.wav

This accepts an audio (ie. sagan.wav) from processing and outputs a folder called testing_output_images




Inside the Obamanet folder:

run: python3 pix2pix.py --mode test --output_dir test_output/ --input_dir testing_output_images/ --checkpoint checkpoints/output/

This productes a folder called /test_output/images that contains images of 1) Drawn in mouth representation and 2) The real mouth representation (outputs)




Inside images folder (/obamanet/test_output/images):

run: ffmpeg -r 30 -f image2 -i %d-outputs.png -vcodec mpeg4 -c:v copy output_video.mp4

This action combines the images into a video




Inside a folder containing both the audio (sagan.wav) and video (output_video.mp4):

run: ffmpeg -i output_video.mp4 -i sagan.wav -c:v copy -c:a aac -strict experimental output.mp4

This combines the audio and video files






To train a set of images in a directory (ie. c_train) :

training: Requires mouth (drawing) and mouth (real) side by side

run:  python3 pix2pix.py --mode train --output_dir output --max_epochs 1 --input_dir c_train --which_direction AtoB
