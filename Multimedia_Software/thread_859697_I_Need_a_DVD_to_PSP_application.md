---
title: "I Need a DVD to PSP application"
date: 2008-07-14
forum: Multimedia Software
---

### Post by cmpunk on 2008-07-14
I need a FREE application that lets me rip a DVD and put it on my PSP. I want the file to be a small and pretty good quality.

And remember, I want it to be FREE. (I would also prefer it to be a .deb file)

Can someone help me?

---

### Post by fenian on 2008-07-14
I use Handbrake to rip/compress DVD,it's not a .deb but pretty easy to set up ,just copy and paste the instructions below (instructions are for Ubuntu 8.04 Hardy).

First get the medibuntu version of ffmpeg (makes more codecs available),but first remove any old ffmpeg,open a terminal and enter...

> sudo apt-get remove ffmpeg

then enter...

> 
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

then enter...

> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

the enter...

> sudo apt-get install ffmpeg

Next install the dependencies Handbrake copy and paste this command...

> sudo apt-get update && sudo apt-get install automake build-essential jam libdvdcss2-dev libtool subversion yasm zlib1g-dev libbz2-dev dvdbackup xmlto texinfo g77 gfortran libgtk2.0-dev nasm doxygen libsdl1.2-dev gfortran-multilib gcc-multilib g++-multilib libesd0-dev libgtk1.2-dev libfftw3-dev electric-fence

next install Handbrake and gtk gui with the following commands (enter each line seperately)
> 
svn co svn://svn.handbrake.fr/HandBrake/trunk HandBrake
cd HandBrake
./configure
make
sudo make install
cd Handbrake/gtk
./autogen.sh
make
sudo make install 

The program should now be available from the menu Application>Sound & Video>HandBrake
there are presets for PSP video.More info can be found[ here ]("http://trac.handbrake.fr/wiki")and[here]("http://handbrake.fr/").

---

### Post by monaro800 on 2008-07-14
i suggest breaking up sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update  as this caused issues for me, suggest running it as follows

sudo apt-get update 

 sudo apt-get install medibuntu-keyring  
  
    sudo apt-get update 

answering YES to the questions :)

---

