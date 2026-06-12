---
title: "VIA Chrome9 integrated graphics"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by ronacc on 2006-11-03
Has anyone got chrome9 graphics working as anything but "vesa) ?
if so please tell how or atleast what.

---

### Post by kipeloff on 2007-03-13
I have got this chipset working on Edgy 6.10 with 'via' drivers.
I have used this nice
[tutorial]("http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/")
Thanks to the author.
The exact syntax however does not work for me good.

First of all I have uninstalled these packages to prevent incosistency or conflicts with drivers,
sudo apt-get remove xserver-xorg-video-via xserver-xorg-video-unichrome

Then you should install packages required by the particular driver. Required packages are listed in the documentation for every driver on [page]("http://www.viaarena.com/")
sudo apt-get install build-essential libxinerama-dev x11proto-xinerama-dev libxvmc-dev sysutils tofrodos

Prepare and install all packages required by these,
sudo apt-get build-dep xserver-xorg-video-via
sudo apt-get build-dep xorg 

Download driver from the viaarena  [page]("http://www.viaarena.com/")

Use 'root' to perfrom other actions,
extract download driver,
tar zxvf *name*

Go to the directory,
cd *name*src

Run on the console to get current kernel version
uname -r 

Modify ./makedriver and ./vinstall_2D on any text editor, find all places, where Ubuntu Edgy is listed with kernel version. In my case, there were older kernel listed rather that I have.
Set results from 'uname -r' there.

Run ./makedriver
that will take some time to compile driver.


Run 'ldconfig, to re-index libraries.

Installation script creates folder on root directory with /*name*
cd /*name*

Run /vinstall_2D
It should finalize the installation and put correct configuration to xorg configuration file after restart or gdm/kdm restart 'via' drivers should be used and graphics runs hugely better comparing to vesa.

---

### Post by stefe on 2007-07-09
cannot find the drivers..... there is only a pdf file

---

### Post by Nkari on 2007-10-09
I noticed that the Download from the VIA website seemed to only have the documentation in it too.

Thought I may try the command line way, but it seems to be for an older version and may be incorrect for 7.04.

I just wanted to set a machine up at work with Ubuntu so people could play with it and decide if they really wanted to pay to get windows on their new computers. 

Video is the only thing not recognised properly, so I can not set the widescreen LCD to the correct resolution

---

