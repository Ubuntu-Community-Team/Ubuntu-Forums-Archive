---
title: "Authentication for Downloading MP3 Codecs"
date: 2011-01-13
forum: Multimedia Software
---

### Post by Flood-X on 2011-01-13
Let me begin by saying that this is my first day of using Ubuntu after just successfully installing it with the help of a post by one of the forum members.

I wanted to listen to some of my MP3's to see if they worked. So I double-clicked on one of them and got a message saying "search for suitable plugin?"

I clicked on "search." It then searches plugin packages and tells me to select the packages for installation. The available packages are:
gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-mp3
gstreamer0.10-plugins-ugly

I checked off all of them and then clicked "install." I then get a window to "confirm installation of restricted software." I click on confirm and then get a window saying "authenticate to install or remove software, you need to authenticate" and it asks for a password. I'm assuming they mean my login password. I enter my password and click "authenticate" but then nothing happens. The password entry space goes away but the authenticate window remains. I don't know if I'm supposed to manually close it after clicking authenticate. But I tried that. What happens when I close the "authenticate" window is that another window appears saying "applying changes" but then I get a message saying "requires installation of untrusted packages. The action would require the installation of packages from not authenticated sources." The details lists these:
gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-ugly liba52-0.7.4 libavcodec52 libavformat52 libavutil50 libdvdnav4 libdvdread4 libgsm1 libid3tag0 libmad0 libmpeg2-4 liboil0.3 libopencore-amrnb0 libopencore-amrwb0 libpostproc51 libschroedinger-1.0-0 libsidplay1 libswscale0 libtwolame0 libva1 libvpx0

If I click on ok. Another window appears saying: "none of the selected packages were installed."

Anyone know what's going on? Are these typical errors?

---

### Post by BicyclerBoy on 2011-01-13
You must not have entered the sudo password.

Those packages are all good.
You are installing the non-free codecs used as plugins by that player (RhythmBox ?).
Windoze & OS-X include licences/royalties for some codecs & a DVD player.

RhythmBox uses gstreamer.
The libav* libraries come from ffmpeg.

Ubuntu does not come installed with non-free codecs.
To use mp3 (Frauhoffer) or MPEG to make a movie long than 10 minutes requires a royalty payment or licence from MPEG-LA. I'm not joking...

You can install from synaptic package manager
ubuntu-restricted-extras
libdvdcss  (medibuntu)

I think it does the same thing & is less messy (less windoze like)

---

### Post by Flood-X on 2011-01-14
Thank you so much for your reply.

Let me explain in detail what I tried. I noticed that the default program to open mp3 files is the "movie player" program that comes installed with Ubuntu. I chose to open them with the "rhythmbox music player" and the same window came up asking if I wanted to search for packages/codecs. This time they installed and now my mp3 files work.

Although it worked, I'm wondering why, for the sake of learning.

Also, would you recommend using another media player rather than the pre-installed media players? When I use windows, I use the k-lite codec pack from [www.codecguide.com](www.codecguide.com)

Also, is there anything I have to do to be able to open realplayer (audio and video) files?

---

### Post by tmafuve on 2011-03-17
I have a problem downloading mp3 files from a website. I'm on Ubuntu 10.10 and use google chrome and firefox 4 as my browsers on a Dell Latitude 131L laptop. If I right click on the file I want to download there is no option to download or save the file; I only get options to save link or open link in a new tab.
I don't get this problems when using Internet explorer on a windows desktop. I just right click and I get the option to save file as.
Any help will be appreciated

---

