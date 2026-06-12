---
title: "Karmic driving me crazy! video codec package problems"
date: 2009-12-05
forum: Multimedia Software
---

### Post by superyounan1 on 2009-12-05
When I first upgraded to Karmic I noticed that I lost all MPEG4 playback capability - any sort of Divx or Xvid type video I had wouldn't play in any video player including VLC and totem.

Totem would offer to search for compatible codecs but would say it couldn't find any.

After exhaustive searching I ended up installed package "libavcodec52", and voala, everything works perfectly again! But then I noticed that "devede" was being held back from updates, so I ran:
```
sudo apt-get dist-upgrade
```
and it removed "libavcodec52" and installed "libavcodec-extra-52" in place of it, this brought me back to square one! No videos worked in any player, arghhhhh!

To fix it i tried purging "ubuntu-restricted-extras" and re-installing it, and it tries to fix the problem for me:
```
The following packages were automatically installed and are no longer required:
  wine1.2 ttf-tahoma-replacement ttf-symbol-replacement wine1.2-gecko
  libmpg123-0 winbind
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libavcodec52
The following packages will be REMOVED:
  libavcodec-extra-52
The following NEW packages will be installed:
  libavcodec52 ubuntu-restricted-extras
0 upgraded, 2 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B/3,977kB of archives.
After this operation, 36.9kB disk space will be freed.
Do you want to continue [Y/n]? Y

```

So I ran it, videos work again, and devede is being held back again:
```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  devede
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

Anyone else having this problem?

---

### Post by superyounan1 on 2009-12-08
bump

---

### Post by Yellow Pasque on 2009-12-08
Go into Synaptic and mark devede for upgrade. You will get a more specific error message.

---

### Post by mc4man on 2009-12-08
The upgrade path from jaunty to karmic is littered with broken players, incompatible codecs, outputs and what not.

The eventual solutions can vary depending on what you brought forward and have done/added since.

What I'd do at this point

If you have any ppa's enabled then open System -> Admin. ->  software sources -> third party and disable them. Then click close and reload.

open up synaptic and search ffmpeg and mark for removal ffmpeg if installed and **all** it's libs that are installed ( starting with libavcodec52, ending at libswscale0

then search devede and mark for removal, search mplayer and also remove it and mencoder. ( if mplayer-nogui is installed also remove

You'll have some plugins and possibly players also removed, just re- install afterwards.

After they're all marked then click apply.

When done, close synaptic, then open a terminal and run 

```
sudo apt-get update && sudo apt-get install devede
```

Then this to restore, fill in some plug-ins

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse

```

 If all goes well then install any other players, plugins,  ect.

Note:

Don't run sudo apt-get install ubuntu-restricted-extras, it's somewhat borked.

If you have cairo-dock installed then expect problems with  vlc

Don't use the openshot -dev. ppa

---

### Post by i386DX on 2009-12-09
Thanks mc4man, that did the trick (I had more or less the same problem)

---

### Post by superyounan1 on 2009-12-19
Thank you so much for your reply, I followed your instructions, then re-enabled the medibuntu karmic repository and tried to get myself back in working order but unfortunately it did no help.

VLC still says:
```
No suitable decoder module:
VLC does not support the audio or video format "XVID". Unfortunately there is no way for you to fix this.

```

Totem:
```

**No packages with the requested plugins found**
The requested plugins are:
XVID MPEG-4 decoder

```

audio plays, video does not.

So I tried install libavcodec5, here is what it displays:
```

sudo apt-get install libavcodec52
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vcdimager libsvga1 libdvbpsi5 dvdauthor libvlc2 libiso9660-5 vlc-data libtar libvlccore2 libvcdinfo0 libebml0
  libmatroska0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  devede gstreamer0.10-ffmpeg libavcodec-extra-52 libavformat-extra-52 libk3b6-extracodecs mencoder mplayer-nogui vlc
  vlc-nox vlc-plugin-pulse
The following NEW packages will be installed:
  libavcodec52
0 upgraded, 1 newly installed, 10 to remove and 0 not upgraded.
Need to get 3,971kB of archives.
After this operation, 25.8MB disk space will be freed.

```

I wasn't it expecting to remove so much, but I tried it out anyway.
I tried to run a video and Totem now recommended installing package gstreamer0.10-ffmpeg.
I installed it, but the damn thing still wouldn't play! and I got the message 
```
**An error occurred** 
The playbck of this movie requires a XVID MPEG-4 decoder plugin which is not installed
```

I seem to be in much worse shape than before. I'll keep fiddling with it and report back.

In the meantime, if anyone has any other suggestions, for the love of god let me know. Otherwise I suppose I'll run a clean install, but I just don't have the time to organize enough for that.

Sigh, Windows, where are you baby? I'm sorry! Cmon, lets talk

---

### Post by superyounan1 on 2009-12-19
I spoke too soon! 

I re-installed VLC and everything seems fine all of a sudden, across the board!

```
sudo apt-get install vlc
Reading package lists... Done                      
Building dependency tree                           
Reading state information... Done                  
The following packages were automatically installed and are no longer required:
  vcdimager libsvga1 libopenjpeg2 libamrnb3 dvdauthor libamrwb3                
Use 'apt-get autoremove' to remove them.                                       
The following extra packages will be installed:                                
  vlc-nox vlc-plugin-pulse                                                     
Suggested packages:                                                            
  mozilla-plugin-vlc videolan-doc                                              
The following NEW packages will be installed:                                  
  vlc vlc-nox vlc-plugin-pulse                                                 
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.                 
Need to get 0B/4,390kB of archives.                                            
After this operation, 11.6MB of additional disk space will be used.            
Do you want to continue [Y/n]? Y
```

---

### Post by superyounan1 on 2009-12-21
and now everything is broken again. out of the blue. I didn't even run any updates. WTF

I installed libavcodec52 again and it seems to be working:

```

sudo apt-get install libavcodec52                                          
Reading package lists... Done                                                                         
Building dependency tree                                                                              
Reading state information... Done                                                                     
The following packages will be REMOVED:                                                               
  libavcodec-extra-52 libavcodec-unstripped-52                                                        
The following NEW packages will be installed:                                                         
  libavcodec52                                                                                        
0 upgraded, 1 newly installed, 2 to remove and 0 not upgraded.                                        
Need to get 0B/3,971kB of archives.                                                                   
After this operation, 139kB disk space will be freed.                                                 
Do you want to continue [Y/n]? Y                                                                      
(Reading database ... 235098 files and directories currently installed.)                              
Removing libavcodec-unstripped-52 ...                                                                 
dpkg: libavcodec-extra-52: dependency problems, but removing anyway as you requested:                 
 mplayer depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:
  Package libavcodec52 is not installed.                                                                      
  Package libavcodec-extra-52 is to be removed.                                                               
 libavformat52 depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:
  Package libavcodec52 is not installed.                                                                            
  Package libavcodec-extra-52 is to be removed.                                                                     
 libavformat52 depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:                                                                                                                    
  Package libavcodec52 is not installed.                                                                               
  Package libavcodec-extra-52 is to be removed.                                                                        
 libavformat52 depends on libavcodec52 (>= 4:0.5+svn20090706) | libavcodec-extra-52 (>= 4:0.5+svn20090706); however:   
  Package libavcodec52 is not installed.                                                                               
  Package libavcodec-extra-52 is to be removed.                                                                        
 libavformat52 depends on libavcodec52 (<< 4:0.5+svn20090706-99) | libavcodec-extra-52 (<< 4:0.5+svn20090706-99); however:                                                                                                                    
  Package libavcodec52 is not installed.                                                                               
  Package libavcodec-extra-52 is to be removed.                                                                        
 vlc-nox depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:         
  Package libavcodec52 is not installed.                                                                               
  Package libavcodec-extra-52 is to be removed.                                                                        
 libk3b6-extracodecs depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:                                                                                                                    
  Package libavcodec52 is not installed.                                                                               
  Package libavcodec-extra-52 is to be removed.                                                                        
 gstreamer0.10-ffmpeg depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:                                                                                                                   
  Package libavcodec52 is not installed.                                                                               
  Package libavcodec-extra-52 is to be removed.                                                                        
 mplayer-nogui depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:   
  Package libavcodec52 is not installed.                                                                               
  Package libavcodec-extra-52 is to be removed.                                                                        
 libquicktime1 depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however:   
  Package libavcodec52 is not installed.                                                                               
  Package libavcodec-extra-52 is to be removed.                                                                        
 libxine1-ffmpeg depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-extra-52 (>= 3:0.svn20090303-1); however: 
  Package libavcodec52 is not installed.                                                                               
  Package libavcodec-extra-52 is to be removed.                                                                        
Removing libavcodec-extra-52 ...                                                                                       
Processing triggers for libc-bin ...                                                                                   
ldconfig deferred processing now taking place                                                                          
Selecting previously deselected package libavcodec52.                                                                  
(Reading database ... 235078 files and directories currently installed.)                                               
Unpacking libavcodec52 (from .../libavcodec52_4%3a0.5+svn20090706-2ubuntu2_i386.deb) ...                               
Setting up libavcodec52 (4:0.5+svn20090706-2ubuntu2) ...                                                               

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


```

---

### Post by ronaldpianist on 2009-12-22
Thank you from heart for your wise advice, mc4aman!

This solved all my problems with the broken XVid playback on my EEE PC running Karmic UNR.

Greetings from the Czech Republic!
R.

---

### Post by superyounan1 on 2010-01-02
I found that libavcodec-extra-52 was not working for me because it was looking for a library file called libx264.so.67, but I looked in /usr/local/lib and saw I have libx264.so.68. 

In order to have things function with package libavcodec-extra-52 instead of libavcodec52 I had to create a link:

```

desktop:/usr/lib$ ls -altr | grep libx264
-rw-r--r--   1 root root   599548 2009-07-08 06:26 libx264.so.68
lrwxrwxrwx   1 root root       22 2010-01-02 10:39 libx264.so.67 -> /usr/lib/libx264.so.68

```

I found a bug report that discusses this, but it was marked as invalid:
[https://bugs.launchpad.net/ubuntu/+source/x264/+bug/475933](https://bugs.launchpad.net/ubuntu/+source/x264/+bug/475933)

My guess is this problem affects only a handful of people that upgraded to Karmic.

---

### Post by mc4man on 2010-01-02
> My guess is this problem affects only a handful of people that upgraded to Karmic.

No, there is no libx264-68 in ubuntu and repo libs would install to /usr/lib, not /usr/local/lib

So somehow you installed a shared x264 to /usr/local, which depending on how done can be ok or not

Generally you can have multiple versions of libx264 installed (1 install per core version) to satisfy dependencies of sources built off of them, and if built/installed correctly will cause no issues

The karmic repo libavcodec52 (whether normal or extra) depends on libx264-67, which really should be installed.
If you can get away with linking to a 68 version with no issues so be it, though certainly not proper.

see screen to see how various shared libx264's can coexist ( the bottom package is the current x264 built as static to /usr/local for use as a standalone x264 and building off of.

---

### Post by volamoot on 2010-01-03
I recently had the same problem, so i just added the File "Ubuntu Restricted Extras" and it did the trick. I hope they fix the problem soon... Windows seems to have alot of the same problems at this time. (The Ubuntu Restricted Extras can be downloaded from the ubuntu software center at the botton of the main application menu)

Good Luck

---

### Post by Vincent_Lin on 2010-01-05
Somehow my openshot would not even start.  Here is the error message on the command line:
```
girls@girls:~$ openshot
Added /usr/share/openshot to system path
--------------------------------
   OpenShot (version 0.9.54)
--------------------------------
/usr/share/openshot/windows/SimpleGladeApp.py:340: GtkWarning: gtk_toolbar_set_icon_size: assertion `icon_size != GTK_ICON_SIZE_INVALID' failed
  return gtk.glade.XML(self.glade_path, root, domain)
A new frmMain has been created
Traceback (most recent call last):
  File "/usr/bin/openshot", line 50, in <module>
    main()
  File "/usr/share/openshot/openshot.py", line 57, in main
    form1 = MainGTK.frmMain(project=current_project, version=info.SETUP['version'])
  File "/usr/share/openshot/windows/MainGTK.py", line 160, in __init__
    self.settings.load_settings_from_xml()
  File "/usr/share/openshot/windows/preferences.py", line 207, in load_settings_from_xml
    xmldoc = xml.parse(settings_path)
  File "/usr/lib/python2.6/xml/dom/minidom.py", line 1918, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0

```

Someone please help.

Thanks.

Vincent

---

### Post by Vincent_Lin on 2010-01-11
Hi all,

I really could not find any more information why this openshot would not run. So when I learned that 1.0.0 has been released, I jumped into install it. I set up PPA and downloaded the key, and apt-get to install openshot, and I assume that necessary depedencies will be updated as well. This part went fine.

Then I started up openshot. Still no go.

So I have to dig into the command line error messages and try to figure out what happened.

The python and xml parsing stopped at line #211 of a file /usr/lib/python2.6/xml/dom/expatbuilder.py.
parser.parse ("", True)

The error message said that
xml.Parser.expat.ExpatError: no element found: line 1, column 0

So, I went for help of google and figured that this function parser.parse either takes two arguments (inputstream, flag) or a blank for one argument only. Obviously the prgrammer wanted to give this function an empty argument, and it should have one empty argument only.

So I chagnged this line into
parser.parse ("")

and then I fired up openshot. It works!! I then exported about 1 minute of footage(linked together from 2 MTS files) from my NEC HD camcorder, and exported into mp4 with 1080P resolution at 29.97 frame rate. It works.

So now it is back to normal again. (Yeah I had openshot workintg before but it stopped for no known reason).

Please help to take a look at this piece of code, and please tell me if I was doing it right.

I really enjoy using this program.

Cheers,

Vincent

---

