---
title: "gstreamer plugins installed, Banshee still won't play"
date: 2011-08-18
forum: Multimedia Software
---

### Post by skr5e on 2011-08-18
I'm trying to use Banshee to play an mp3. My sound works normally, but when I open a file with Banshee, the application will open but nothing will actually play. The slider bar isn't moving and under it says "Idle", clicking the "play button" will also not work.

gstreamer plugins are installed, that seemed to be the main solution offered to this problem but it hasn't done much to solve my particular problem. Any other ideas?

---

### Post by cottfcfan on 2011-08-18
You may need more plugins.
Try in a terminal:
```
sudo apt-get install ubuntu-restricted-extras
```
That should give you everything you need for audio & video.
It may help to make sure the canonical partner repos are enabled and updated in synaptic first.

---

### Post by skr5e on 2011-08-18
Tried getting the restricted extras, no change.

How do I update canonical partner repos? I tried apt-get update, still no change.

---

### Post by skr5e on 2011-08-18
bump

tried other suggestions since I've been searching around...uninstall/reinstall, same old problem. :confused:

---

### Post by garvinrick4 on 2011-08-18
What is your version of Ubuntu?
```
lsb_release -a
```I will give you list of all I have installed.

---

### Post by skr5e on 2011-08-18
root@bt:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.2 LTS
Release:        10.04
Codename:       lucid

---

### Post by garvinrick4 on 2011-08-18
Take a look in Synaptics package manager and type in gstreamer in search box
and see if you have all these installed.  I do get mp3 play also checked to make sure.
gstreamer0.10-alsa               
gstreamer0.10-ffmpeg                
gstreamer0.10-fluendo-mp3         
gstreamer0.10-gnonlin               
gstreamer0.10-nice              
gstreamer0.10-plugins-bad         
gstreamer0.10-plugins-bad-multiverse        
gstreamer0.10-plugins-base            
gstreamer0.10-plugins-base-apps            
gstreamer0.10-plugins-good           
gstreamer0.10-plugins-ugly            
gstreamer0.10-plugins-ugly-multiverse        
gstreamer0.10-pulseaudio           
gstreamer0.10-tools               
gstreamer0.10-x

---

### Post by garvinrick4 on 2011-08-18
Run this in a terminal and will give you a list of installed in alphabetical order
might be easier to check which ones installed. Results will be in home.
```
sudo dpkg --get-selections > installedsoftware 
```

---

### Post by skr5e on 2011-08-18
gstreamer0.10-alsa                
gstreamer0.10-ffmpeg                
gstreamer0.10-fluendo-mp3            
gstreamer0.10-gnonlin                
gstreamer0.10-nice                
gstreamer0.10-pitfdll                
gstreamer0.10-plugins-bad            
gstreamer0.10-plugins-bad-multiverse        
gstreamer0.10-plugins-base            
gstreamer0.10-plugins-base-apps            
gstreamer0.10-plugins-good            
gstreamer0.10-plugins-ugly            
gstreamer0.10-plugins-ugly-multiverse        
gstreamer0.10-pulseaudio            
gstreamer0.10-tools                
gstreamer0.10-x                     

ok I found which ones were missing and installed them. AND it's working perfectly. Thanks so much, that's 2/2 problems this forum has helped me solve, you guys are awesome ;)

---

### Post by garvinrick4 on 2011-08-18
Good, now if you will go up to Thread tools in upper right and mark your Thread
as Solved so others may benefit from with same. Enjoy your Ubuntu skr5e.

---

### Post by cottfcfan on 2011-08-19
Just as a matter of interest, when you said that you "tried" getting the ubuntu-restricted-extras package, did it install or not?

And as for the canonical partners repo, go into synaptic package manager, click settings, repositories, other software, and make sure the top 4 repos are ticked. Then close and click reload.
Everything then should be up to date.

---

