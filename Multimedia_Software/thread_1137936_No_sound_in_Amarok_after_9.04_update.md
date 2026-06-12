---
title: "No sound in Amarok after 9.04 update"
date: 2009-04-26
forum: Multimedia Software
---

### Post by GuiGuy on 2009-04-26
Sound is otherwise playing find. Just don't have it in Amarok 2. 

Any ideas before 9.04 drives me completely insane? :)

Thanks

---

### Post by thewolfman on 2009-04-26
Do you have all the codecs you need, xine plugins, gstreamer and the like, check out if any need to be installed and see if that helps.

---

### Post by GuiGuy on 2009-04-26
> **thewolfman said:**
> Do you have all the codecs you need, xine plugins, gstreamer and the like, check out if any need to be installed and see if that helps.

No, that's all there. As stated above, sound in other apps (Xine etc) is fine. Just Amarok2 :(

---

### Post by dubski on 2009-04-26
This worked for me:

1. Install phonon-backend-xine.
2. Remove phonon-backend-gstreamer.

-=dubski=-

---

### Post by victorgreen on 2009-04-26
Thank you so much; Ive been trying to figure out why I wasnt getting any sound. I just upgraded to Jaunty 64, using straight Ubuntu. It was giving me hda_nvidia not found, reverting to default. 

Of course now that it makes noise, Ive noticed it got rid of all my statistics, labels, and means to make a playlist based on the labels and other dynamic criterion. I hate this program

---

### Post by dave r on 2009-04-26
> **dubski said:**
> This worked for me:

1. Install phonon-backend-xine.
2. Remove phonon-backend-gstreamer.

-=dubski=-

:P Worked for me too, Thank you

---

### Post by GuiGuy on 2009-04-26
> **dubski said:**
> This worked for me:
1. Install phonon-backend-xine.
2. Remove phonon-backend-gstreamer.

Thanks, but I'd already checked that installation. 

So, no luck. 

regards

---

### Post by GuiGuy on 2009-05-02
It's hard to remain positive with all the issues I am having since upgrading (??) to jaunty. 

Is anyone able to give me any useful suggestions as to what else I might try to get sound out of amacrok?

Please note 
[LIST]
[*]sound is working fine in every other application
[/LIST]

---

### Post by siddharth_moghe on 2009-05-02
same here ! no sound in amarok2 only, everything else works ! 

phono backend is already the latest one

siddharth@novice:~$ sudo apt-get install phonon-backend-xine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libqt4-opengl libmtp8 libgpod4-nogtk librdf0 kdebase-runtime-data-common libqt4-test kdelibs5 amarok-common kde-icons-oxygen libexiv2-5
  librasqal1 libsoprano4 redland-utils kdelibs5-data libqt4-svg libstreamanalyzer0 kdelibs-bin libpq5 libstreams0 exiv2 soprano-daemon kdebase-runtime-data
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  phonon-backend-xine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/154kB of archives.
After this operation, 569kB of additional disk space will be used.
Selecting previously deselected package phonon-backend-xine.
(Reading database ... 124103 files and directories currently installed.)
Unpacking phonon-backend-xine (from .../phonon-backend-xine_4%3a4.3.1-0ubuntu3_i386.deb) ...
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
                                                    <unknown program name>(4863)/ KStartupInfo::createNewStartupId: creating:  "novice;1241322152;756156;4863_TIME0" : "unnamed app"
                       kbuildsycoca4 running...
                                               Setting up phonon-backend-xine (4:4.3.1-0ubuntu3) ...

---

### Post by GuiGuy on 2009-05-03
> **siddharth_moghe said:**
> same here ! no sound in amarok2 only, everything else works ! 


Maybe this needs to be posted as a bug. But whenever I do that I get howled down for being a klutz and an idiot, so I'll let someone else do it. ;)

Cheers

---

### Post by Nat90 on 2009-05-03
This worked for me: 

OSS HOWTO:
1) Download this file: [[URL=http://www.fileupyours.com/view/77985/libphonon.conf]("http://www.fileupyours.com/view/77985/libphonon.conf")[/URL]
2) Put it in:~/.config/kde.org/ (where ~/ means your home directory) You may need to create the kde.org directory
3) If you don't have phonon-backend-xine install it.
sudo apt-get install phonon-backend-xine
4) Restart Amarok 2 and have fun.

It think the problem was that Amarok couldn't handle multiple ALSA channels, so if another program used ALSA, Amarok broke.
What this does is set Amarok in OSS, so if everything else is in ALSA(as it should be by default) it should work just fine.

---

### Post by ovcica on 2009-05-03
Had the same problem. The bar was moving, but there was no sound. The sound was working fine in every other app. After removing phonon-backend-gstreamer (phonon-backend-xine was already installed) it all works fine.

---

### Post by GuiGuy on 2009-05-03
> **Nat90 said:**
> This worked for me: 

OSS HOWTO:


Thank you. That worked great!

It does raise the question though; why do they do this? I mean, break something by the misconfiguration of a .conf file most of us don't know about??

But again, many thanks.

---

### Post by BLWedge09 on 2009-05-03
> **Nat90 said:**
> This worked for me: 

OSS HOWTO:
1) Download this file: [[URL=http://www.fileupyours.com/view/77985/libphonon.conf]("http://www.fileupyours.com/view/77985/libphonon.conf")[/URL]
2) Put it in:~/.config/kde.org/ (where ~/ means your home directory) You may need to create the kde.org directory
3) If you don't have phonon-backend-xine install it.
sudo apt-get install phonon-backend-xine
4) Restart Amarok 2 and have fun.

It think the problem was that Amarok couldn't handle multiple ALSA channels, so if another program used ALSA, Amarok broke.
What this does is set Amarok in OSS, so if everything else is in ALSA(as it should be by default) it should work just fine.

This worked great for me as well. What's odd is that just a day or two ago, I had an Installation that was Ubuntu Jaunty 64 with the kubuntu-desktop added on top of it.  Sound in Amarok worked just fine there.  Last night I wiped out and installed Kubuntu Jaunty 64 directly and had this problem.  Anyway, this fixed it.  Thanks for the tip!

---

### Post by GuiGuy on 2009-05-03
> **BLWedge09 said:**
> This worked great for me as well. What's odd is that just a day or two ago, I had an Installation that was Ubuntu Jaunty 64 with the kubuntu-desktop added on top of it.  Sound in Amarok worked just fine there.  

That was my situation. It stopped working on the second reboot after upgrading.

---

### Post by siddharth_moghe on 2009-05-03
well even that doesnt work. Let me know what other fileoutputs u need !to check whats wrong with my system ! 

can anyone upload the amarok 1.4 deb file ?

---

### Post by GuiGuy on 2009-05-03
> **siddharth_moghe said:**
> well even that doesnt work. Let me know what other fileoutputs u need !to check whats wrong with my system ! ?

I had to reboot, so I presume you did that too?

---

### Post by nexx on 2009-05-03
Just deleted the .kde file in my home directory and amarok2 is playing again.

---

### Post by xloadedx on 2009-05-03
The xine instead of gstreamer package fixed mine.  Thanks a billion.  It was so puzzling because sound was working virtually everywhere else.

---

### Post by markbuntu on 2009-05-04
What is going on is that Amarok2 is using xine through phonon so you need the phonon-xine package. With amd64 this package is installed along with amarok so that seems to be strictly a 32 bit issue. If you are using gnome there is no way to set the phonon default so you need to set the xine default.

With my 64bit Jaunty I still had no sound on Amarok so I got xine-ui and changed the sound output to pulseaudio (you need to need to be master of the known universe to see these settings). amarok and vlc are now working properly with pulse.

---

### Post by GuiGuy on 2009-05-04
> **markbuntu said:**
> 
With my 64bit Jaunty I still had no sound on Amarok so I got xine-ui and changed the sound output to pulseaudio (you need to need to be master of the known universe to see these settings). amarok and vlc are now working properly with pulse.

Thanks for the explanation. Useful.

Cheers.

---

### Post by siddharth_moghe on 2009-05-04
may be you can downgrade to amarok 1.4 like the good'ol days


[http://ubuntuforums.org/showthread.php?t=1144859](http://ubuntuforums.org/showthread.php?t=1144859)

here is how you can do it :popcorn:

---

### Post by maxphil on 2009-05-05
I had this exact problem and fixed it in 1min after reading post #11. :P

Thx guys
[]'s

---

### Post by flysen on 2009-05-07
I think you have to uninstall "gstreamer0.10-plugins-bad"
and maybe install phonon-backend-xine.
That was the case for me when upgrading from 8.10 --> 9.04
//Fredrik

---

### Post by Chaos_Spear on 2009-05-08
> **Nat90 said:**
> This worked for me: 

OSS HOWTO:
1) Download this file: [[URL=http://www.fileupyours.com/view/77985/libphonon.conf]("http://www.fileupyours.com/view/77985/libphonon.conf")[/URL]
2) Put it in:~/.config/kde.org/ (where ~/ means your home directory) You may need to create the kde.org directory
3) If you don't have phonon-backend-xine install it.
sudo apt-get install phonon-backend-xine
4) Restart Amarok 2 and have fun.

It think the problem was that Amarok couldn't handle multiple ALSA channels, so if another program used ALSA, Amarok broke.
What this does is set Amarok in OSS, so if everything else is in ALSA(as it should be by default) it should work just fine.

Thank you so much!  I agree, Amarok just didn't share ALSA well.  I don't get why they didn't leave a setting within Amarok to choose whether to run on ALSA or OSS, but whatever I guess...

---

### Post by Kouki on 2009-05-09
> **dubski said:**
> This worked for me:

1. Install phonon-backend-xine.
2. Remove phonon-backend-gstreamer.

-=dubski=-

Brilliant!  I've been trying to get amarok fixed for about 4 hours and this has done it.  Thanks for sharing your resolution :guitar:

I kept searching for 'Amarok won't play mp3', which didn't take me to this thread.  I searched for those terms because Amarok streamed internet radio fine, but just wouldn't play mp3's.

Hopefully by adding that above paragraph, this thread will appear when other users search for similar search terms to those I did.

Thanks again.

---

### Post by wimbou on 2009-05-22
Hi all,

installing phonon-backend-xine did it for me.

Have a nice day 

Wim

---

### Post by z0mbie on 2009-05-28
> **Nat90 said:**
> This worked for me: 

OSS HOWTO:
1) Download this file: [[URL=http://www.fileupyours.com/view/77985/libphonon.conf]("http://www.fileupyours.com/view/77985/libphonon.conf")[/URL]
2) Put it in:~/.config/kde.org/ (where ~/ means your home directory) You may need to create the kde.org directory
3) If you don't have phonon-backend-xine install it.
sudo apt-get install phonon-backend-xine
4) Restart Amarok 2 and have fun.

It think the problem was that Amarok couldn't handle multiple ALSA channels, so if another program used ALSA, Amarok broke.
What this does is set Amarok in OSS, so if everything else is in ALSA(as it should be by default) it should work just fine.


Kudos to you my friend. This worked perfect. Thanks a bunch!!!

---

### Post by nithin19484 on 2009-06-01
> **markbuntu said:**
> What is going on is that Amarok2 is using xine through phonon so you need the phonon-xine package. With amd64 this package is installed along with amarok so that seems to be strictly a 32 bit issue. If you are using gnome there is no way to set the phonon default so you need to set the xine default.

With my 64bit Jaunty I still had no sound on Amarok so I got xine-ui and changed the sound output to pulseaudio (you need to need to be master of the known universe to see these settings). amarok and vlc are now working properly with pulse.

Thanks man!!! This worked for me..

---

### Post by Kimos on 2009-06-07
> **dubski said:**
> This worked for me:

1. Install phonon-backend-xine.
2. Remove phonon-backend-gstreamer.

-=dubski=-

I'm running Gnome and using Amarok. I just updated from 8.04 to 9.04. This cleared the problem up for me. Thanks dubski!

---

### Post by carolinason on 2009-06-18
installing libxine1-all-plugins worked for me. running in oss

---

### Post by marcomaravigna on 2009-06-22
i am experiencing the same problem, i have already installed xine backend, but still i am not getting any sound. has anyone found a solution in the meanwhile?
emme

---

### Post by miniyak on 2009-07-18
phonon switch from gstreamer to xine fixed Amarok for me but broke Miro

thats probably something i should have expected huh?

any tips on how to make this solution friendly with other applications?

---

### Post by miniyak on 2009-07-18
Macromaravinga, just the xine backend from the add/remove application is ineffective in solving this problem. I have this installed before i started playing with amarok and still had the same problem.

If you have yet to, try using synaptic (system>administration>synaptic package manager) Then use dudski's suggestion

---

### Post by Durden on 2009-07-19
> **carolinason said:**
> installing libxine1-all-plugins worked for me. running in oss

THANK YOU! This worked for me

---

### Post by runninglot on 2009-10-11
I had the same problem. Despite having phonon-backend-xine already installed and having removed phonon-backend-gstreamer, it still did not work. I changed the default audio driver in xine to pulse audio, but this did not change anything either. What did solve the problem (possibly in conjunction with the previous changes---I did not check) was the removal of ~/.config/kde.org/libphonon.conf. In ~/.config/kde.org/ now only the file Phonon-Xine.xine.conf resides.

---

