---
title: "Nvidia MX4000 glx-96 driver poor video playback"
date: 2009-05-14
forum: Multimedia Software
---

### Post by domoso on 2009-05-14
Ok, this nvidia driver really pisses me off. I need it to get TV-out working. But, I'm noticing a problem. When I'm playing a video, avi, dvd, whatever, there are two horizontal lines that appear to moderate to heavy motion during playback. These lines appear on a monitor as well as when playing tv-out. 

I confirmed that it is an issue with the nvidia-glx-96 driver by deactivating it. After deactivating I am not able to detect the horizontal lines. 

Any ideas?

---

### Post by Crafty Kisses on 2009-05-14
Did you install the nVidia drivers from Synaptic or from nVidia's official website?

---

### Post by domoso on 2009-05-14
I installed through System -> Hardware Drivers and activated it through that panel.

---

### Post by Crafty Kisses on 2009-05-14
Now I'm going to suggest you download and install the driver off of nVidia's website, not sure if this will actually solve the problem, but it's worth a shot. I'm just assuming your on a 32-bit machine, so I'll provide the 32-bit driver link:
[LIST]
[*]32-bit: [http://us.download.nvidia.com/XFree86/Linux-x86/96.43.11/NVIDIA-Linux-x86-96.43.11-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.11/NVIDIA-Linux-x86-96.43.11-pkg1.run)
[/LIST]
So you want to grab that real quick, now as always before I give instructions on how to install the official driver, you probably want to backup your X just in case anything happens, so run the following:
```
sudo cp /etc/X11/xorg.conf ./xorg.conf.backup
```
That will backup your X, now what you want to do is remove the old nVidia driver you have, which you can run the following:
```
sudo apt-get --purge remove nvidia-glx-96 nvidia-kernel-common nvidia-settings
```
That will completely remove the old driver and the settings along with it, now it's time to install the new nVidia driver. You need to stop your X, so you need to run the following command:
```
sudo /etc/init.d/gdm stop
```
Now I'm just going to guess the file is called "NVIDIA-Linux" and it's saved to your **desktop**, so remember substitute your information when you run the command, so here's the example command:
```
cd ~/Desktop
chmod +x NVIDIA-Linux.run
sudo ./NVIDIA-Linux.run
```
Now once you have confirmed everything you can run:
```
sudo /etc/init.d/gdm start
```
Then you should be set. If you have any issues with the official nVidia driver you can uninstall it by running the following:
```
sudo sh NVIDIA* --uninstall
```
Remember where the * is you need to put the right driver information and it will remove the nVidia drivers. If the build doesn't work, you might need the "build-essential" package and you can install that by running the following:
```
sudo apt-get install build-essential
```
Once you have the nVidia drivers installed and running you can access your card settings by running:
```
gksudo nvidia-settings
```
I'm hoping this may help you.

---

### Post by domoso on 2009-05-14
The above instructions resulted in low graphics mode being run. They system can't load the NVIDIA kernel module.

I think I'll give envyng a try and see if that can load that. Really, I don't know why it has to be so difficult to load a different video driver in an OS that for the most part makes Linux a breeze. 

I'll let you know how it turns out. And, btw, thanks for your help. Please don't think I'm directing my frustration above at you.

---

### Post by domoso on 2009-05-14
Ok, I uninstalled the driver via envyng. Envyng did not report the latest driver as being available. After the uninstall and a reboot I re-ran the NVIDIA*.run installation. It reported that the 96.43.11 driver was already installed. So, I reinstalled it anyway. After the driver was reinstalled I rebooted and then went to the loo. When I came back gnome was up and running. I checked the Nvidia X Server Settings and it appears to be loaded.

However, the 2 horizontal lines are still visible during playback of videos. The horizontal lines do not move, they just appear during motion in the videos. The lines are together and appear at about the bottom of the first 1/3 of the screen. It's rather annoying. 

Is there a convenient way of getting a screen capture so that I can show it to everyone?

Any more suggestions?

---

### Post by domoso on 2009-05-14
Changed my color depth from 24bit to 16bit. It seems to have improved the situation. However, the lines are still perceptible and lower on the screen now. 

I don't understand why this should be a problem. It feels like a performance issue. However, I've had much slower computers playing video flawlessly in the past. The type of video I'm playing is nothing HD. Just typical mpeg, dvd stuff. Top is reporting cpu utilization at ~15% when playing. 

On thing that I noticed with this or any NVIDIA driver available to Intrepid Ubuntu and this video card: The overlay is viewable remotely via VNC. However, with the stock Ubuntu driver, it is not. And in the past with other computers even using older driver on older Ubuntu's the overlay was never viewable remotely via VNC. So, I'm thinking it might be something with the overlay? Unfortunately, I don't have enough knowledge to be more specific or know how to address this or know if this is normal or if this is a change in the way Ubuntu is displaying video. I've read of some of the changes in video display on the Intel graphics thread for Jaunty video issues. So, you tell me.

---

### Post by domoso on 2009-05-14
I'm thinking I should probably move down to a pre8.0 version of Ubuntu. Maybe that would help?

---

### Post by domoso on 2009-05-14
The issue with the horizontal lines is NOT an NVIDIA driver issue. It's a Ubuntu issue. I ditched Ubuntu and loaded an old Debian Etch disk. Using the same NVIDIA-96.43.11 driver the video is perfect on Debian Etch with a lot less resource utilization as well. Thanks for the help though. I just got tired of Ubuntu's refusal to do anything other than what it set itself up to do.

---

