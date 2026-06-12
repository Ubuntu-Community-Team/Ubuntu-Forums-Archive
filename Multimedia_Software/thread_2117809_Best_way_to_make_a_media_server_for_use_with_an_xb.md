---
title: "Best way to make a media server for use with an xbox 360"
date: 2013-02-19
forum: Multimedia Software
---

### Post by safedave on 2013-02-19
install ubuntu 12.04

update system

install gparted

sudo apt-get install gparted

after this i opened gparted and selected the drive i wanted to use (and format with ntfs)
ntfs will allow you to share folders with both ubuntu and windows based computers to be honest i wouldnt do what other forums
say and instal ext4 because windows does not understand ext4 or any other ext for that matter

install storage device manager from ubuntu software centre
once you got storage manager you can open it from typing it into the dashboard
now the next lesson you have to remember is with drive mounting and this is my findings is you need to make sure you only
mount drives sdb sdc sdd sde (sda is the drive of your operating system)
once you got your drives mounted the next think to do is reboot to check to see if it works fine
if successful move onto the next step

i found installing samba from the sharing section much easier for this i went to my home directory right click on the selected folder
(or drive) properties, share now click share it will ask you to install samba once its done selected the 2 tick boxes saying
"allow other to create and delete files in this folder" and "guest access (for people who do not have an account)"

this is now setup you should be able to see your drives via a windows computer, via the network section (try to share these folders)
if this fails to work please check in the storage device manager to see if that tick box is unchecked in the assistance section of the drive options
for read only.

next for the media streaming this is the best software for configuring and streaming media SERVIIO

now this is how you install this

bare in mind you need a whole lot of distributions to get the final product to work all these steps MUST BE PERFORMED

first java

sudo apt-get install default-jre

next FFmpeg

sudo apt-get install ffmpeg libavcodec-extra-53 libavformat-extra-53

Download Serviio

wget [http://download.serviio.org/releases/serviio-1.1-linux.tar.gz](http://download.serviio.org/releases/serviio-1.1-linux.tar.gz)

extract serviio

tar xvf serviio-1.1-linux.tar.gz

you now need to create a config file for serviio to do this you need to go to a terminal and input the following

sudo gedit /etc/init/serviio.conf

in this file you need to input this 

start on started networking
script
   /home/raveon/serviio-1.1/serviio.sh
end script

save the file and exit it

The upstart system now starts the serviio server as soon as all networking jobs have been started:

sudo /etc/init.d/networking restart

You can now get a list of all jobs registered with upstart by issuing:

initctl list

and you should get something like:

serviio start/running, process 1009

if it is already running, otherwise it says:

serviio stop/waiting

You can start and stop the job via:

sudo start serviio

and

sudo stop serviio

now to make ya server a remote version i used windows desktop assistance

for this i used these code:

sudo apt-get install xrdp

now you will have issues with this so before you use this you need to do 3 more steps

echo "gnome-session --session=ubuntu-2d" > ~/.xsession

and then

sudo apt-get install gnome-session-fallback

then restart 

now that is it your server should run headless i left my keyboard on and jus stuck it in the corner of the room

believe me this worked for me on a very minumal machine :D

---

