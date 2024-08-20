# Raspberry-Pi-configuratio-for-machine-learning-and-IoT
This repository provides a guide to configuring a Raspberry Pi for machine learning and IoT projects. It includes steps to install TensorFlow, OpenCV, run machine learning algorithms, and boot from an SSD using a HAT. Ideal for both beginners and advanced users, this guide helps you set up and optimize your Raspberry Pi for various applications.

# Installing Arduino ide –
•	First download the tar.zx file from site
•	Go to download folder through terminal and run command ---- tar –xf  <downloaded file name>
•	run ls command you see one new folder name with Arduino 
•	go to that folder through cd 
•	run command - sudo  ./install.sh


# Setup of installing older version of python– we downgrade our python version because in new version of rasbien os  python 3.11 which does not support tensorflow on raspberry pi – so we shift to 3.10 version 
video link - https://youtu.be/vekblEk6UPc?si=Z9n4b2V_AP-ievJR
STEPS –
1.	Run the easy installer 
curl https://pyenv.run | bash
2. Add pyenvto .bashrc:
Edit the .bashrc with the command 
sudonano ~/.bashrc
3. Add the following three lines to the bottom of the .bashrc file:
export PATH="$HOME/.pyenv/bin:$PATH" 
eval "$(pyenvinit --path)" 
eval "$(pyenvvirtualenv-init -)" 
4. Restart the terminal
exec $SHELL 
5. Install system packages
sudo apt-get install --yes libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev llvm libncurses5-dev libncursesw5-dev xz-utilstk-dev libgdbm-dev lzmalzma-dev tcl-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev wget make openssl
6. Update pyenv
pyenv update 
7. Install python versions
pyenv install --list 
pyenvinstall  3.10.13
8. Set python verion
Cd Desktop
Mkdir   AI_Codes
 cd AI_Codes
pyenvlocal  3.10.13

# Install TensorFlow and OpenCV
1.	python3 -m pip install virtualenv
python3 -m virtualenv env 
source env/bin/activate
2.	sudo apt-get install -y libhdf5-dev libc-ares-dev libeigen3-dev gccgfortran libgfortran5 libatlas3-base libatlas-base-dev libopenblas-dev libblas-dev liblapack-dev cython3 libatlas-base-dev openmpi-bin libopenmpi-dev python3-dev build-essential cmake pkg-config libjpeg-dev libtiff5-dev libpng-dev libavcodec-dev libavformat-dev libswscale-dev libv4l-dev libxvidcore-dev libx264-dev libfontconfig1-dev libcairo2-dev libgdk-pixbuf2.0-dev libpango1.0-dev libgtk2.0-dev libgtk-3-dev libhdf5-103 libqt5gui5 libqt5webkit5 libqt5test5 python3-pyqt5

3.	python3 -m pip install -U wheel mock six

4.	Select the .whl from - https://github.com/PINTO0309/Tensorflow-bin/tree/main/previous_versions

Select "view raw" then copy the URL 
Run: 1.-wget [Raw file URL] 
2.-sudo chmod +x [Raw file URL] 
3.-./[Tensorflow file] 
4.-tensorflow python3 -m pip install tensorflow-[Your version here].whl
5.      exec $SHELL
6.     source env/bin/activate
7.     pip install opencv-contrib-python (more libraries and customization)
8.     pip install opencv-python 

Checking ---
python import tensorflow as tf
tf.__version__ quit()

# If above step of open cv is not working then do this –
(This process take 2 hours)
1.	sudo apt-get install libgtk2.0-dev pkg-config
2.	pip uninstall opencv-python
3.	git clone https://github.com/opencv/opencv.git
4.	cd opencv
5.	mkdir build
6.	cd build 
7.	cmake ..
8.	make 
9.	sudo make install

# Installing LLM on raspberry pi –
1.	Curl  -fsSLhttps://ollama.com/install.sh  |  sh
2.	ollama run tinyllama
for exit from ollama model – run
1.	/bye
Libraries which I installed –
1.	pip install jupyter
2.	

# Installing torch and torchvision on raspberry pi-
1.	sudo apt get install python3-pip
2.	pip3 install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu116



# Edge Impulse installation ----
The installation on the Raspbian OS is a bit longer than ubuntu, because you need to change the installation path so that you do not require root/administrator permissions while execution of the CLI. Go ahead and follow the instructions for installation.
Instructions for manually changing default directory
To minimize the chance of permissions errors, you can configure npm to use a different directory. In this example, you will create and use hidden directory in your home directory.
•	Back up your computer.
•	On the command line, in your home directory, create a directory for global installations:
$ curl -sL https://deb.nodesource.com/setup_20.x | sudo -E bash -
$ sudo apt-get install -y nodejs

Check if the version is v20 or above
$ node -v
$ curl -fsSL https://raw.githubusercontent.com/arduino/arduino-cli/master/install.sh | sh

If it returns that the directory is not on path, type
npm config get prefix

Whatever output you get-add in place of home/dave/work
export PATH=/home/dave/work:$PATH
The above script installs arduino cli
$ npm config get prefix

This command should return usr/local or \usr. Now follow the below steps, to set it on path so you do not require administrative permisiions
$ mkdir ~/.npm-global

Configure npm to use the new directory path:
$ npm config set prefix '~/.npm-global'
In your preferred text editor, open or create a ~/.profile file and add this line:
export PATH=~/.npm-global/bin:$PATH

On the command line, update your system variables:
$ source ~/.profile

Now install the cli:
$ npm install -g edge-impulse-cli


# Bossac error on arm64 for WIO terminal, SEEED SAMD Boards -----  
 
1.		Click the following link to download a version of the Seeed package index file that has the modification I mentioned above:
package_seeeduino_boards_aarch64_index.json (2.6 KB)
2.	Wait for the download to finish.
3.	Copy the downloaded file to the folder at the following path:
4.	/home/<username>/.arduino15/
(Where <username> is your Linux username)
  The .arduino15 folder may be hidden by default in your file manager and terminal.
5.	Start Arduino IDE if it is not already running.
6.	Select File > Preferences from the Arduino IDE menus.
The "Preferences" dialog will open.
7.	Click the icon on the right side of the "Additional Boards Manager URLs" field of the dialog.
The "Additional Boards Manager URLs" dialog will open.
8.	Add the following URL on a new line of the field in the "Additional Boards Manager URLs" dialog:
9.	file:///home/<username>/.arduino15/package_seeeduino_boards_aarch64_index.json
  You must leave the standard Seeed Boards Manager URL 5 in the field in addition to the URLs you are adding, so don't overwrite it.
10.	Replace the <username> in that URL with your Linux username.
11.	Add the following URL on a new line of the field in the "Additional Boards Manager URLs" dialog:
12.	https://adafruit.github.io/arduino-board-index/package_adafruit_index.json
 This URL must be added because it contains the information needed to install the replacement adafruit:bossac@1.8.0-48-gb176eee tool dependency.
13.	Click the "OK" button.
The "Additional Boards Manager URLs" dialog will close.
14.	Click the "OK" button.
The "Preferences" dialog will close.
15.	Select Tools > Board > Boards Manager... from the Arduino IDE menus.
The "Boards Manager" dialog will open.
16.	Wait for the updates to finish, as shown by the messages printed at the bottom of the "Boards Manager" dialog.
17.	Scroll down through the list of boards platforms until you find the "Seeed SAMD Boards - Linux ARM 64-bit" entry. Click on it.
Some buttons will appear on the entry.
18.	Click the "Install" button on the "Seeed SAMD Boards - Linux ARM 64-bit" entry.
19.	Wait for the installation to finish successfully.
20.	Click the "Close" button on the "Boards Manager" dialog.
The "Boards Manager" dialog will close.

# Install btop++ on Raspberry Pi

1 - wget -qO btop.tbz https://github.com/aristocratos/btop/releases/latest/download/btop-armv7l-linux-musleabihf.tbz
2 - sudo tar xf btop.tbz --strip-components=2 -C /usr/local ./btop/bin/btop
3 - rm -rf btop.tbz


# How to boot Raspberry Pi 5 from NVMe M.2 SSD
1-	Site link - https://notenoughtech.com/raspberry-pi/boot-raspberry-pi-5-from-nvme/
2-	Youtube link - https://youtu.be/MwrdwbYI_7M?si=Be4VI220Xiu5gnOW


# How to create banner in linux –
1.	sudo apt install figlet lolcat
2.	sudo nano  ~/.bashrc
3.	figlet –f slant –c “Scientech” | lolcat
4.	figlet –f digital –c “Partner in Your Technology” | lolcat
