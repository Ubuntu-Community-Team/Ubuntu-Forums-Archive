---
title: "HOWTO: Streaming HD 264 MKV Video with NVIDIA + VDPAU Over Wireless Network"
date: 2012-09-08
forum: Multimedia Software
---

### Post by strid3r on 2012-09-08
If you've ever tried to stream HD Movies from another computer or a media server over Windows File Sharing and a wireless network, you know how slow the videos can be. Using the following, I went from slow and choppy slideshows to crisp and smooth videos. I wanted an easy way to watch my 720p movies on my laptop and this is a guide for making it very simple.

This guide assumes you have a recent NVIDIA card that supports VDPAU (Hardware Acceleration).

Check here to see if your Nvidia Card is supported:

[URL="http://www.mythtv.org/wiki/VDPAU#Supported_Cards"]http://www.mythtv.org/wiki/VDPAU#Supported_Cards
[/URL]
If you haven't already, Install The Proprietary NVIDIA Drivers:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

[B]Next Install VDPAU:
[/B]
Note: YouTube and other flash videos may appear with a blue tint after enabling VDPAU. There's a patch for that, just enable this ppa:

```
sudo add-apt-repository ppa:tikhonov/misc
sudo apt-get update
sudo apt-get install libvdpau1 vdpau-va-driver

```



[B]Accessing the Videos on the Network:
[/B]

We will mount the Network Share onto a folder on /media/. This will make it a lot easier when trying to play the videos later.

Install smbfs to be able to mount the folder and create a folder (mount point) for the share::

```
sudo apt-get install smbfs
sudo mkdir /media/SambaShare/
```


Next, mount the share to /media/SambaShare/

USERNAME is the user on the windows computer that is sharing the files. Also, you cannot mount a file within the shared folder, it must be the shared folder itself.

```
sudo smbmount //192.168.2.28/projects /media/SambaShare/ -o user=USERNAME
```


Refer to the first Answer Here for More details:
[http://askubuntu.com/questions/137011/how-to-mount-a-samba-shared-folder-ubuntu-x-ubuntu]("http://askubuntu.com/questions/137011/how-to-mount-a-samba-shared-folder-ubuntu-x-ubuntu")


[B]Creating a script to mount the shares
[/B]

This next step makes it so you don't have to type in the previous code every time you restart your computer. You could add it to your /etc/fstab/ to have it mount when you start your computer but I chose to make it into a script and add it to /bin/ so I can mount with a simple command. It's easier than it sounds.

Open a text editor to save the script:
```
sudo gedit /bin/mountshares
```

Paste the following and be sure to modify the second line to your settings.

```
#!/bin/bash
sudo smbmount //192.168.2.28/projects /media/SambaShare -o user=USERNAME

```

Now make it executable.

```
sudo chmod +x /bin/mountshares
```

Now anytime you want to mount the network share, just type into terminal

```
sudo mountshares
```


This is 10x easier than remembering all of that code. If you have extra shares that you want to mount, just edit /bin/mountshares as root.





Now we will install MPlayer and be much closer to playing that HD movie in lag-free super smooth quality.

```
sudo apt-get install mplayer
```

The reason why the videos were choppy before is because of two things, the first was lack of hardware acceleration which we took care of in the first half. The second is a low cache size. Why MPlayer works so well is because you can specify both.

We're going to make a second script that makes playing the movies soo much easier. We're going to add it to /bin/ as we did before.

Open a text editor to save the script:
```
sudo gedit /bin/playnetmovie
```

Now paste the following:

```
#!/bin/bash
echo "Playing Movie Starting at Time $1"
mplayer -ss $1 -vo vdpau -vc ffh264vdpau -fs -cache 99999 -cache-min $2 "$3"
```

Now we're going to make it executable

```
sudo chmod +x /bin/playnetmovie
```


So that you don't have to go through all those folders to get to the movie files, make a symbolic link to the videos folder on your windows computer:

```
mkdir NetVids
ln /media/SambaShare/place/where/videos/are/stored/ ~/Videos/NetVids 
```

Now we can finally play our first movie. The syntax for playnetmovie is as follows:

```
playnetmovie 00:00:00 30 ~/Videos/NetVids/Movie/filename.mkv
```

The 00:00:00 is the start time. If you want to start from the beginning of the movie, just type 0 instead of 00:00:00. If you are continuing the movie from where you left off, just type in the time according to this format HH:MM:SS. The 30 is the percent of the cache that MPlayer should fill up before starting playback. The buffer size for playnetmovie is pre-set to 99,999 KB so if you do any more than 30%, you'll be waiting quite a while. If you're on a fast network you can probably do 10, if you are on a slower network you can bump it up to 50.

So that's it! Anytime after this you want to stream your HD videos, just type in two commands.

First mount the network drive:

```
sudo mountshares
```

Then play the movie:

```
playnetmovie 0 20 ~/Videos/Movie/filename.mkv
```

This also works for streaming HD movies over the internet:

```
playnetmovie 0 20 http://website.com/file/directory/yourmovie.avi
```

For MPlayer Controls:

[http://www.keyxl.com/aaa2fa5/302/MPlayer-keyboard-shortcuts.htm]("http://www.keyxl.com/aaa2fa5/302/MPlayer-keyboard-shortcuts.htm")


:popcorn:

Enjoy!




*** This also works for MP4, AVI, and any other HD Video you wish to watch ***



References:

Enabling VDPAU [http://linuxforums.org.uk/index.php?topic=4232.0]("http://linuxforums.org.uk/index.php?topic=4232.0")
Mounting Windows Shares [http://askubuntu.com/questions/137011/how-to-mount-a-samba-shared-folder-ubuntu-x-ubuntu]("http://askubuntu.com/questions/137011/how-to-mount-a-samba-shared-folder-ubuntu-x-ubuntu")
MPlayer + VDPAU [http://ubuntuforums.org/showthread.php?t=1037625]("http://ubuntuforums.org/showthread.php?t=1037625")

---

