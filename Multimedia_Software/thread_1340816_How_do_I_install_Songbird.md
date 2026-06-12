---
title: "How do I install Songbird?"
date: 2009-11-29
forum: Multimedia Software
---

### Post by PDA1 on 2009-11-29
I've downloaded Songbird from this link- [http://getsongbird.com/](http://getsongbird.com/)

I extract it using Archive Manage.

It extracts ok but Songbird doesn't run.  There are no install instructions in the Songbird folder.

Does it really matter which folder I extract Songbird to?

I'm using Ubuntu 9.10.  I think my processor is an x86 or something like that....not sure.

Is there an easy way to get Songbird onto my machine?

Man, it's pretty bad when you have no idea how to work with Linux stuff.

---

### Post by aysiu on 2009-11-29
Probably easier to install the .deb file:
[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

---

### Post by PDA1 on 2009-11-30
Here's what happens when I download and try to install.  (I followed step 2 in the link you mentioned above).

1. Screen pops up reading- LAUNCH APPLICATION.  This link needs to be open with an application.  Send to:  (then it lists "apturl" and "Choose an application")

I selected "apturl" as I don't know what else to do.

I click OK....

It downloads something (I assume it's songbird).

Then I get this error;

*Could not download all repository indexes*

*The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.*

In the bottom box of the above mentioned message reads; 

[I] Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/pp/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu-wine/pp/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
 Some index files failed to download, they have been ignored, or old ones used instead.


[/I]So, I click  OK anyway.
Then is says, Songird already installed.

Well, I can't find Songbird anywhere on my computer.

What should I do now?

---

### Post by PDA1 on 2009-11-30
For whatever miraculous reason I got Songbird to run.

Somewhere on here I saw that I should use Terminal and type "Songbird" in the directory where Songbird is located.

Songbird starts and runs but if I close Terminal- Songbird shuts down.

How do I fix that?

---

### Post by aysiu on 2009-11-30
> **PDA1 said:**
> For whatever miraculous reason I got Songbird to run.

Somewhere on here I saw that I should use Terminal and type "Songbird" in the directory where Songbird is located.

Songbird starts and runs but if I close Terminal- Songbird shuts down.

How do I fix that?
There should be a Songbird launcher in your Applications menu.

If you want to launch it from the terminal, just put an *&* sign at the end of the command: ```
Songbird &
``` Don't forget you can also use Alt-F2 to launch applications (no *&* necessary then).

---

### Post by PDA1 on 2009-11-30
Your method doesn't work.

I can only run Songbird by using the method I mentioned above about using Terminal and going to the directory where Songbird is located and then typing Songbird.  Then it runs.  Here are the error messages I get in Terminal when it starts up.  However, it does run well.

Is there a way to modify the Songbird (egg icon) icon in Applications > Sound & video to start Songbird?  



earl@earl-laptop:~/Downloads/Songbird$ songbird

(songbird-bin:3830): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsthdvparse.so': /usr/lib/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gst-0.10/gst/__init__.py", line 193, in <module>
    from _gst import *
ImportError: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_alloc_trace_live_all

(songbird-bin:3830): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:3830): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdeinterlace.so': /usr/lib/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_format_parse_caps_interlaced

(songbird-bin:3830): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstasfmux.so': /usr/lib/gstreamer-0.10/libgstasfmux.so: undefined symbol: gst_tag_list_add_value

(songbird-bin:3830): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libresindvd.so': /usr/lib/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command

(songbird-bin:3830): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/gstreamer-0.10/libgstschro.so: undefined symbol: gst_adapter_masked_scan_uint32

(songbird-bin:3830): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstlibvisual.so': /usr/lib/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:3830): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmpegdemux.so': /usr/lib/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:3830): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstrawparse.so': /usr/lib/gstreamer-0.10/libgstrawparse.so: undefined symbol: gst_video_format_new_caps_interlaced

(songbird-bin:3830): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdv.so': /usr/lib/gstreamer-0.10/libgstdv.so: undefined symbol: gst_tag_list_new_full

---

### Post by aysiu on 2009-12-01
I think the issue is that you're still trying to use the precompiled binary instead of properly installing Songbird.

Forget *apturl*.

Just follow the instructions in this YouTube video:
[http://www.youtube.com/watch?v=5vePK-JxszA](http://www.youtube.com/watch?v=5vePK-JxszA)

---

### Post by mick222 on 2009-12-01
getdeb now reqires you to add the repositories follow this link  install getdeb  then install songbird [http://www.getdeb.net/updates/#how_to_install](http://www.getdeb.net/updates/#how_to_install)

---

### Post by PDA1 on 2009-12-01
I downloaded and installed GetDeb.

Then, I downloaded Songbird.

Since I don't want to use apturl it asks for OTHER program.

Which do I use?  Getdeb?  

If it's GetDeb.....where do I find it on my computer?  I can't find any reference to it all.

---

### Post by aysiu on 2009-12-01
> **PDA1 said:**
> I downloaded and installed GetDeb.

Then, I downloaded Songbird.

Since I don't want to use apturl it asks for OTHER program.

Which do I use?  Getdeb?  

If it's GetDeb.....where do I find it on my computer?  I can't find any reference to it all. Watch the video I linked to. It shows you every single step.

---

### Post by aysiu on 2009-12-01
Alternatively, you can just download [this file](http://archive.getdeb.net/getdeb/ubuntu/pool/apps/s/songbird/songbird_1.2.0-1~getdeb2_i386.deb) and double-click it.

That won't add the proper repository, so you won't get updates, but at least Songbird will be easily installed.

---

### Post by PDA1 on 2009-12-01
Great video!

I get to the end of using Synaptic Manager part but....


The terminal window doesn't open.

Here's the error message I get;



Failed to execute child process "/home/earl/Downloads/Songbird/" (No such file or directory)


Any ideas?

---

### Post by kindafunnylookin on 2009-12-01
> **aysiu said:**
> Watch the video I linked to. It shows you every single step.
 I found your replies to be spot on and very helpful. As usual.

---

### Post by PDA1 on 2009-12-01
Man, I really must be doing something wrong.

The ONLY way I can get Songbird to run is if I use Terminal and type in "songbird".

It'll run then.  But, Songbird will only run IF I keep Terminal open.  If I close Terminal....then Songbird closes.

Also, there is no "songbird" icon on any of my Applications folders.....not even in Accessories.  Yes, I know it's supposed to be in Sound and Video.

Could there be some trouble, or something not set correctly in Administration?

---

### Post by aysiu on 2009-12-01
> **PDA1 said:**
> Great video!

I get to the end of using Synaptic Manager part but....


The terminal window doesn't open.

Here's the error message I get;



Failed to execute child process "/home/earl/Downloads/Songbird/" (No such file or directory)


Any ideas? That's weird. If you're using Synaptic, I'm not sure why it's looking for anything in the Downloads folder. It should be fetching Songbird off the GetDeb repositories (online) and not anywhere locally.

Can you paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then post the output back here (especially if there are any error messages)? ```
sudo apt-get update && sudo apt-get install songbird
```

---

### Post by dewapur on 2009-12-01
hey, last night I also download the tar.gz file from [http://getsongbird.com](http://getsongbird.com) then extract it to my home directory. I just double clicked the script songbird.sh to run songbird and it's just singing with no problem. I'm with hardy currently.

---

### Post by PDA1 on 2009-12-01
> **aysiu said:**
> That's weird. If you're using Synaptic, I'm not sure why it's looking for anything in the Downloads folder. It should be fetching Songbird off the GetDeb repositories (online) and not anywhere locally.

Can you paste this command into [the terminal]("http://www.psychocats.net/ubuntu/terminal") and then post the output back here (especially if there are any error messages)? ```
sudo apt-get update && sudo apt-get install songbird
```


This is what I got.....


earl@earl-laptop:~$ sudo apt-get update && sudo apt-get install songbird
[sudo] password for earl: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_CA          
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_CA              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic Release.gpg                            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main Translation-en_CA                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_CA    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_CA      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_CA    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release.gpg                        
Ign [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Translation-en_CA             
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/universe Translation-en_CA  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates Release.gpg         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic Release                     
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release                            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main Packages                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main Sources                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/restricted Sources                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/universe Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                        
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/apps Packages                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/universe Sources             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
songbird is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
earl@earl-laptop:~$ songbird

---

### Post by aysiu on 2009-12-01
That's odd. So Songbird is already installed.

Can you paste in these commands and paste the output back here? (Warning: the first command will ask for your password and take at least a minute to execute) ```
sudo updatedb
locate songbird
which Songbird
which songbird
uname -a
```

---

### Post by PDA1 on 2009-12-01
> **aysiu said:**
> That's odd. So Songbird is already installed.

Can you paste in these commands and paste the output back here? (Warning: the first command will ask for your password and take at least a minute to execute) ```
sudo updatedb
locate songbird
which Songbird
which songbird
uname -a
```


I hate to do this but here's the output- ```
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/bg-splitter-horizontal.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/bg-splitter-vertical.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/bg-table-header.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/bg-text-input.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/bg-tree-drop-feedback.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/button-checkbox.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/button-column-picker.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/button-radio.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/button-scale-thumb.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/button-scroll-down.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/button-scroll-left.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/button-scroll-right.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/button-scroll-up.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/button-spin-down.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/button-spin-up.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/button-twisty.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/icon-default-favicon.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/icon-error.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/icon-loading-large.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/icon-loading.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/icon-sort-ascending.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/icon-sort-descending.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/base-elements/icon-success.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser/bg-status-bar-button.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser/bg-status-bar.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser/icon-autoscroll.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser/icon-link-playable.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser/icon-popup-blocker.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser-tab-bar/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser-tab-bar/bg-media-tab.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser-tab-bar/bg-scroll.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser-tab-bar/bg-selected-media-tab.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser-tab-bar/bg-selected-tab.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser-tab-bar/bg-tab-bar.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser-tab-bar/bg-tab-delimiter.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser-tab-bar/bg-tab.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser-tab-bar/button-close.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser-tab-bar/icon-drop-indicator.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser-tab-bar/icon-scroll-left.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/browser-tab-bar/icon-scroll-right.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/device/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/device/battery-charged.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/device/battery-charging.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/device/battery-draining.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/device/battery-empty.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/device/battery-left.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/device/battery-right.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/device/bg-capacity-bar-left.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/device/bg-capacity-bar-right.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/device/bg-capacity-bar.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/device/bg-legend.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/device/button-eject.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/device/button-info.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/device/device-progress-error.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/device/icon-generic-device.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/display-pane/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/display-pane/bg-empty.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/display-pane/bg-header.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/display-pane/button-addon-picker.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/display-pane/button-content-pane-toggle.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/display-pane/button-maximize.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/display-pane/button-restore.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/display-pane/button-right-sidebar-toggle.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/display-pane/button-service-pane-toggle.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/display-pane/content-pane-bottom.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/display-pane/right-sidebar.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/display-pane/service-pane-bottom.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/find-bar/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/find-bar/bg-find-bar.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/find-bar/button-close.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-eq-slider-bkgd.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-eq-slider.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-faceplate-inactive-left.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-faceplate-inactive-right.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-faceplate-inactive-splash.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-faceplate-inactive.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-faceplate-left.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-faceplate-ratings.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-faceplate-right.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-faceplate.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-media-control-pane-left.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-media-control-pane-right.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-media-control-pane.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-seekbar-buffering-left.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-seekbar-buffering-right.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-seekbar-buffering.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-seekbar-left.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-seekbar-notch.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-seekbar-progress.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-seekbar-right.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-seekbar.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/bg-volume-bar.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/button-faceplate-ratings.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/button-fastforward.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/button-max-volume.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/button-min-volume.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/button-next.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/button-play-pause.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/button-previous.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/button-record.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/button-repeat.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/button-rewind.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/button-seek-thumb.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/button-shuffle.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/button-stop.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/button-volume-thumb.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-control-pane/icon-text-delimiter.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/media-pages/firstrun.css
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/menu/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/menu/bg-check.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/menu/bg-separator.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/menu/dropmarker.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/menu/icon-arrow.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/metadata-editor/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/metadata-editor/button-back.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/metadata-editor/button-forward.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/bg.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/button-close.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/done-hover.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/done.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/face-l.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/face-r.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/faceplate.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/l.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/max-vol.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/min-vol.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/next.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/play-pause.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/previous.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/r.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/remaining.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/tip-hover.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/tip.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/mini-player/vol.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/nav-bar/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/nav-bar/bg-button.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/nav-bar/bg-nav-bar-left.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/nav-bar/bg-nav-bar-right.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/nav-bar/bg-nav-bar.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/nav-bar/button-add-search-service.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/nav-bar/button-add.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/nav-bar/button-back.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/nav-bar/button-clear-search.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/nav-bar/button-forward.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/nav-bar/button-home.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/nav-bar/button-media-page.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/nav-bar/button-reload.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/nav-bar/button-stop.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/nav-bar/dropmarker.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/notification-bar/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/notification-bar/bg-critical.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/notification-bar/bg-info.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/notification-bar/bg-warning.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/notification-bar/button-close.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/notification-bar/icon-blocked-popup.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/notification-bar/icon-web-api.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/os-specific/mac
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/os-specific/unix
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/os-specific/win
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/os-specific/mac/overrides.css
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/os-specific/unix/overrides.css
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/os-specific/win/overrides.css
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/playlist/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/playlist/bg-command-bar.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/playlist/bg-download-done.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/playlist/bg-download.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/playlist/bg-progress-not-started.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/playlist/bg-progress-paused.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/playlist/bg-progress.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/playlist/button-download-left.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/playlist/button-left-error.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/playlist/button-left.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/playlist/button-right.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/playlist/icon-dragging.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/playlist/icon-playing.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/playlist/ratings-readonly.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/playlist/ratings.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/preferences/preferences.css
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/ratings/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/ratings/ratings.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/bg-container-node.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/bg-selected-node.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/bg-service-pane.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/bg-status-bar.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/button-new-node.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/button-service-pane-toggle.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/icon-birdhouse.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/icon-bookmark.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/icon-busy.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/icon-concert.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/icon-device.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/icon-downloads-progress.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/icon-downloads.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/icon-favoritesplaylist.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/icon-folder-closed.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/icon-folder.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/icon-ipod.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/icon-library.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/icon-playlist.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/icon-smartplaylist.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/icon-subscription.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/icon-web-media-history.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/service-pane/twisty.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/smart-playlist/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/smart-playlist/button-add.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/smart-playlist/button-remove.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/splitter/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/splitter/grippy-collapsed-horizontal.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/splitter/grippy-collapsed-vertical.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/splitter/grippy-horizontal.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/splitter/grippy-vertical.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/window/Thumbs.db
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/window/bg-button-box.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/window/bg-resizer-bottom-corner.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/window/bg-title-bar-left.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/window/bg-title-bar-right.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/window/bg-title-bar.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/window/button-close-macos.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/window/button-close.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/window/button-expand-macos.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/window/button-maximize.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/window/button-minimize-macos.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/window/button-minimize.png
/home/earl/.songbird2/67awvyc0.default/extensions/{ca903c4d-574b-476d-b9f1-599bf92ea503}/chrome/skin/window/button-resizer.png
/home/earl/.songbird2/67awvyc0.default/extensions/{edd6a443-1ff2-48db-8efa-33127a62bb22}/chrome
/home/earl/.songbird2/67awvyc0.default/extensions/{edd6a443-1ff2-48db-8efa-33127a62bb22}/chrome.manifest
/home/earl/.songbird2/67awvyc0.default/extensions/{edd6a443-1ff2-48db-8efa-33127a62bb22}/install.rdf
/home/earl/.songbird2/67awvyc0.default/extensions/{edd6a443-1ff2-48db-8efa-33127a62bb22}/chrome/orange-county.jar
/home/earl/.songbird2/67awvyc0.default/fstrees/{4eb3cc6d-07b9-43e6-a315-96f40cf6702a}.tree
/home/earl/.songbird2/67awvyc0.default/gstreamer-0.10/registry.bin
/home/earl/.songbird2/67awvyc0.default/searchplugins/302443a6-adfa-428f-9281-3680411fab7c.xml
/home/earl/.songbird2/Crash Reports/InstallTime20090616030029
/home/earl/Downloads/songbird_1.2.0-1~getdeb2_i386.deb
/usr/bin/songbird
/usr/local/bin/songbird
/usr/local/bin/songbird/DownloadDevice
/usr/share/Songbird/songbird
/usr/share/Songbird/songbird-512.png
/usr/share/Songbird/songbird-bin
/usr/share/Songbird/chrome/songbird.jar
/usr/share/Songbird/chrome/songbird.manifest
/usr/share/Songbird/defaults/preferences/songbird-channel-prefs.js
/usr/share/Songbird/defaults/preferences/songbird-prefs.js
/usr/share/Songbird/defaults/preferences/songbird-zzz-branding.js
/usr/share/Songbird/extensions/albumart@songbirdnest.com
/usr/share/Songbird/extensions/gonzo@songbirdnest.com
/usr/share/Songbird/extensions/rubberducky-dependencies@songbirdnest.com
/usr/share/Songbird/extensions/albumart@songbirdnest.com/chrome
/usr/share/Songbird/extensions/albumart@songbirdnest.com/chrome.manifest
/usr/share/Songbird/extensions/albumart@songbirdnest.com/install.rdf
/usr/share/Songbird/extensions/albumart@songbirdnest.com/chrome/albumart.jar
/usr/share/Songbird/extensions/gonzo@songbirdnest.com/chrome.manifest
/usr/share/Songbird/extensions/gonzo@songbirdnest.com/install.rdf
/usr/share/Songbird/extensions/rubberducky-dependencies@songbirdnest.com/chrome
/usr/share/Songbird/extensions/rubberducky-dependencies@songbirdnest.com/chrome.manifest
/usr/share/Songbird/extensions/rubberducky-dependencies@songbirdnest.com/install.rdf
/usr/share/Songbird/extensions/rubberducky-dependencies@songbirdnest.com/chrome/rubberducky-dependencies.jar
/usr/share/Songbird/searchplugins/songbird-internal-search.xml
/usr/share/applications/songbird.desktop
/usr/share/doc/songbird
/usr/share/doc/songbird/changelog.Debian.gz
/usr/share/doc/songbird/copyright
/usr/share/pixmaps/songbird.png
/usr/share/pixmaps/songbird.xpm
/var/cache/apt/archives/songbird_1.2.0-1~getdeb2_i386.deb
/var/lib/dpkg/info/songbird.list
/var/lib/dpkg/info/songbird.md5sums
/var/lib/dpkg/info/songbird.postinst
/var/lib/dpkg/info/songbird.postrm
/var/lib/dpkg/info/songbird.shlibs
earl@earl-laptop:~$
```

```
earl@earl-laptop:~$ which Songbird
earl@earl-laptop:~$ which songbird
/usr/bin/songbird
``````

earl@earl-laptop:~$ uname -a
Linux earl-laptop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux
earl@earl-laptop:~$
```

---

### Post by aysiu on 2009-12-02
Everything looks good.

Paste this command in ```
/usr/bin/songbird &
``` Wait at least thirty seconds. If Songbird doesn't launch, post the output (any error messages) back here.

If that works, I also want you to try just pasting the command ```
songbird &
``` in as well.

---

### Post by PDA1 on 2009-12-02
Thank you for the help.

I hope the following makes sense.  I deleted some of the repetitive stuff that appeared on the screen.

earl@earl-laptop:~$ /usr/bin/songbird &
[1] 2212
earl@earl-laptop:~$ 
(songbird-bin:2223): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsthdvparse.so': /usr/lib/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gst-0.10/gst/__init__.py", line 193, in <module>
    from _gst import *
ImportError: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_alloc_trace_live_all

(songbird-bin:2223): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:2223): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdeinterlace.so': /usr/lib/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_format_parse_caps_interlaced

(songbird-bin:2223): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstasfmux.so': /usr/lib/gstreamer-0.10/libgstasfmux.so: undefined symbol: gst_tag_list_add_value

(songbird-bin:2223): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libresindvd.so': /usr/lib/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command

(songbird-bin:2223): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/gstreamer-0.10/libgstschro.so: undefined symbol: gst_adapter_masked_scan_uint32

(songbird-bin:2223): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstlibvisual.so': /usr/lib/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:2223): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmpegdemux.so': /usr/lib/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:2223): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstre

TagLib: MPEG::Properties::read() -- Could not find a valid last MPEG frame in the stream.
TagLib: MPEG::Properties::read() -- Could not find a valid last MPEG frame in the stream.
earl@earl-laptop:~$ 
[1]+  Done                    /usr/bin/songbird
earl@earl-laptop:~$ 
earl@earl-laptop:~$ 
earl@earl-laptop:~$ 
earl@earl-laptop:~$ songbird &
[1] 2313
earl@earl-laptop:~$ 
(songbird-bin:2324): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsthdvparse.so': /usr/lib/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gst-0.10/gst/__init__.py", line 193, in <module>
    from _gst import *
ImportError: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_alloc_trace_live_all

(songbird-bin:2324): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:2324): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdeinterlace.so': /usr/lib/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_format_parse_caps_interlaced


earl@earl-laptop:~$ 
[1]+  Done                    /usr/bin/songbird
earl@earl-laptop:~$ 
earl@earl-laptop:~$ 
earl@earl-laptop:~$ 
earl@earl-laptop:~$ songbird &
[1] 2313
earl@earl-laptop:~$ 
(songbird-bin:2324): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsthdvparse.so': /usr/lib/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gst-0.10/gst/__init__.py", line 193, in <module>
    from _gst import *
ImportError: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_alloc_trace_live_all

(songbird-bin:2324): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:2324): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdeinterlace.so': /usr/lib/gstreamer-0.10/libgstdeinterlace.so: undefined symbol: gst_video_format_parse_caps_interlaced

(songbird-bin:2324): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstasfmux.so': /usr/lib/gstreamer-0.10/libgstasfmux.so: undefined symbol: gst_tag_list_add_value

(songbird-bin:2324): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libresindvd.so': /usr/lib/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command

(songbird-bin:2324): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstschro.so': /usr/lib/gstreamer-0.10/libgstschro.so: undefined symbol: gst_adapter_masked_scan_uint32

(songbird-bin:2324): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstlibvisual.so': /usr/lib/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:2324): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmpegdemux.so': /usr/lib/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:2324): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstrawparse.so': /usr/lib/gstreamer-0.10/libgstrawparse.so: undefined symbol: gst_video_format_new_caps_interlaced

(songbird-bin:2324): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstdv.so': /usr/lib/gstreamer-0.10/libgstdv.so: undefined symbol: gst_tag_list_new_full
TagLib: MPEG::Properties::read() -- Could not find a valid last MPEG frame in the stream.
TagLib: MPEG::Properties::read() -- Could not find a valid last MPEG frame in the stream.
TagLib: MPEG::Properties::read() -- Could not find a valid last MPEG frame in the stream.
TagLib: MPEG::Properties::read() -- Could not find a valid last MPEG frame in the stream.
TagLib: MPEG::Properties::read() -- Could not find a valid last MPEG frame in the stream.

---

### Post by aysiu on 2009-12-02
Weird.

This may help you:
[http://ubuntuforums.org/showthread.php?p=7865095#post7865095](http://ubuntuforums.org/showthread.php?p=7865095#post7865095)

---

### Post by bark50 on 2009-12-05
Not sure if I understand the problem, but I this guide was helpful to me for installing Songbird:  [http://www.howtoforge.com/installing_songbird_on_ubuntu_gutsy_gibbon]("http://www.howtoforge.com/installing_songbird_on_ubuntu_gutsy_gibbon")  (Even though the guide is for an older version of Songbird, it worked for me in Karmic.)

If your Songbird is crashing after it starts up, removing libvisual-0.4-plugins as explained in the 3rd post here -> [http://ubuntuforums.org/showthread.php?p=7865095#post7865095]("http://ubuntuforums.org/showthread.php?p=7865095#post7865095") helped me.

---

### Post by PDA1 on 2009-12-05
Doesn't work.

The only thing that consistently works is opening Terminal and typing in "Songbird".

---

