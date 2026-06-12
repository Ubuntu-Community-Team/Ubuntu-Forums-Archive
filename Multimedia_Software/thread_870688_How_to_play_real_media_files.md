---
title: "How to play real media files?"
date: 2008-07-26
forum: Multimedia Software
---

### Post by sam2501 on 2008-07-26
I want to play .rm and .rmvb files on my ubuntu
i dont want to install real player 'cause its buggy & i dont like its interface


is der a alternative to real player like real alternative or klc codec pack in windows

---

### Post by owain123 on 2008-07-29
If you install Alien (RPM to DEB converter), and download RealPlayer11, and convert it, i found that RealPlayer installs a lot better than compiling it.

But if you still don't want to do that, try Mplayer, and get the essential Mplayer codec pack:

[http://www.afreecodec.com/linux/161/mplayer-essential-codec-pack/](http://www.afreecodec.com/linux/161/mplayer-essential-codec-pack/)

copy them into /usr/local/lib/codecs (you might have to make a new directory if 'codecs' doesn't exist).

Also you may need drv4.so.6.0. which you can download.


if this doesn't play them, try this from terminal:

mplayer filename.rm

This will tell you what codecs it couldn't locate, and which directory it tried to locate them in.

hope this helps

---

### Post by silkstone on 2008-07-29
I agree with the OP that Real Player (in Windows) is a pain, but actually the Linux version works well and is not intrusive.

You don't need alien to install it. This is taken from a tutorial on these forums...

--------------

The following steps show how to install Real Player 11 and Mozilla Plugin for Firefox 3.0 browsers running on Hardy Heron.

Download Real Player 11 from:

  [www.real.com](www.real.com)

Open a terminal and change to the directory where the file was downloaded. Grant execute permissions and run the setup using the following commands:

  chmod 770 RealPlayer11GOLD.bin
  sudo ./RealPlayer11GOLD.bin
  

Use the following default installation directory during the installation:

  /opt/real/RealPlayer

The installer will copy the files and create menu shortcuts. Then run the following commands.

  cd /usr/lib/firefox-addons/plugins
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.xpt nphelix.xpt
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.so nphelix.so
  sudo mv /usr/lib/totem/gstreamer/libtotem-complex-plugin.so ~/.

(Note that the original plugin is copied to your home folder so you can reinstall it in the future, if you wish.)

Open Firefox and type about: plugins (without the space) in the address bar. Scroll down and look for the following entry.

  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
  File name: /opt/real/RealPlayer/mozilla/nphelix.so
  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.4005 built with gcc 3.4.3 on Feb 25 2008

If found, your Real Plugin is installed properly!

---

### Post by Mohitgarg on 2008-08-14
can someone help me with realplayer11Gold.bin installation?

I tried to install it without sudo, which failed. Though the directory was created and a log file was created in it
When i tried with sudo, i got this error
"Extracting files for Helix installation...Segmentation fault"

can anyone know why this is happening.

---

### Post by Drakkor on 2008-08-22
I installed alien, but can't find it,or is it cli only ?

---

### Post by cpetercarter on 2008-08-22
Alien is a cli utility, but - unusually - it has rather good "man" pages which explain how to use it.

---

### Post by Chris Musampa on 2008-08-22
FWIW I tried Alien for the realplayer rpm, the conversion appeared to work but installing the redulting deb failed (can't remember).
silkstone's method worked for me.

---

### Post by ubuntu-freak on 2008-08-22
Would be easier to just:
 
**sudo apt-get install gnome-mplayer gecko-mediaplayer non-free-codecs**
 
Presuming you have the [Medibuntu](ubuntuforums.org/showthread.php?t=766683) repo enabled and have removed other audio/video streaming plugins.

---

### Post by Chris Musampa on 2008-08-22
I'll bear that in mind for the future ubuntu-freak, would it enable rp content in opera?

---

### Post by ubuntu-freak on 2008-08-22
> **Chris Musampa said:**
> I'll bear that in mind for the future ubuntu-freak, would it enable rp content in opera?

 
Yup, works with Opera too.

---

### Post by Orfintain on 2008-09-04
> **ubuntu-freak said:**
> Would be easier to just:
 
**sudo apt-get install gnome-mplayer gecko-mediaplayer non-free-codecs**
 
Presuming you have the [Medibuntu](ubuntuforums.org/showthread.php?t=766683) repo enabled and have removed other audio/video streaming plugins.

Does totem interfere?
I assume the helix realplayer does.

If if simple disable the plugins should that deal the interference?
Then Do I need to restart the browser? The entire system?

Also "gnome-mplayer" is eating all my cpu resources after i closed firefox and restarted something gdm keeps popping up using all kinds of CPU h

Any have idea's how I can get my media to work..?

---

### Post by ubuntu-freak on 2008-09-05
> **Orfintain said:**
> Does totem interfere?
I assume the helix realplayer does.

If if simple disable the plugins should that deal the interference?
Then Do I need to restart the browser? The entire system?

Also "gnome-mplayer" is eating all my cpu resources after i closed firefox and restarted something gdm keeps popping up using all kinds of CPU h

Any have idea's how I can get my media to work..?

 
Have you read my [howto](ubuntuforums.org/showthread.php?t=766683)? All my tips and advice are in there. Though, saying that, I'm not sure why your CPU resources are so high, I've not documented anything related to that in my howto. Perhaps there is a conflict, or graphics driver issue. Only the Flash plugin v9 makes my resources sky rocket, so I installed v10 beta 1.

---

### Post by Orfintain on 2008-09-05
> **ubuntu-freak said:**
> Have you read my [howto](ubuntuforums.org/showthread.php?t=766683)? All my tips and advice are in there. Though, saying that, I'm not sure why your CPU resources are so high, I've not documented anything related to that in my howto. Perhaps there is a conflict, or graphics driver issue. Only the Flash plugin v9 makes my resources sky rocket, so I installed v10 beta 1.

Yes I read you're how-to I spent a few days with the different options mplayer, mplayer+realplayer, gecko - couldn't get real player to work , quick time is ok ,and some other things work but real player i have to copy and paste the hyper link to the real player application not a hudge deal but it would be nice if it worked (I posted a few questions in that huge thread too)

My resources only get high when Mplayer gets stuck somewhere and then I have to kill the process..

I can play dvd's and use the fancy desktop settings so Graphics cards seams to be working ok.

My flash player seams to be fine-- running pulse audio now

So i'm still wondering if the totem plugin in would conflict with gecko?

---

### Post by ubuntu-freak on 2008-09-06
> **Orfintain said:**
> Yes I read you're how-to I spent a few days with the different options mplayer, mplayer+realplayer, gecko - couldn't get real player to work , quick time is ok ,and some other things work but real player i have to copy and paste the hyper link to the real player application not a hudge deal but it would be nice if it worked (I posted a few questions in that huge thread too)

My resources only get high when Mplayer gets stuck somewhere and then I have to kill the process..

I can play dvd's and use the fancy desktop settings so Graphics cards seams to be working ok.

My flash player seams to be fine-- running pulse audio now

So i'm still wondering if the totem plugin in would conflict with gecko?

 
Of course the Totem plugin conflicts with the Gecko plugin, but my howto removes it, along with any others that conflict. Do you have RealPlayer installed still? It's plugins conflict also, you can't have 3 different plugins trying to play one RM stream.

---

### Post by Orfintain on 2008-09-06
If I simple disable the plugins should that deal the interference/conflict?
or do i have to uninstall everything else ?

---

### Post by ubuntu-freak on 2008-09-06
> **Orfintain said:**
> If I simple disable the plugins should that deal the interference/conflict?
or do i have to uninstall everything else ?

 
I guess you could uninstall totem-mozilla, then just manually delete RealPlayer's nphelix plugins.

---

### Post by Orfintain on 2008-09-07
> **ubuntu-freak said:**
> I guess you could uninstall totem-mozilla, then just manually delete RealPlayer's nphelix plugins.

What I was asking is if i go in firefox 3 to 
tools>addons>plugins> and I disable the helix plugin(as well as the other non gecko plugs) after going through your how-to is that going to be sufficient ?

Or do i need to uninstall everything else? 

Because the disable isn't working and I'm hesitant to uninstall my realplayer until I find out how gecko works, for example I'm not sure if I will be able to jump to different sections in an hour long podcast

---

### Post by Orfintain on 2008-09-21
> **silkstone said:**
> I agree with the OP that Real Player (in Windows) is a pain, but actually the Linux version works well and is not intrusive.

You don't need alien to install it. This is taken from a tutorial on these forums...

--------------

The following steps show how to install Real Player 11 and Mozilla Plugin for Firefox 3.0 browsers running on Hardy Heron.

Download Real Player 11 from:

  [www.real.com](www.real.com)

Open a terminal and change to the directory where the file was downloaded. Grant execute permissions and run the setup using the following commands:

  chmod 770 RealPlayer11GOLD.bin
  sudo ./RealPlayer11GOLD.bin
  

Use the following default installation directory during the installation:

  /opt/real/RealPlayer

The installer will copy the files and create menu shortcuts. Then run the following commands.

  cd /usr/lib/firefox-addons/plugins
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.xpt nphelix.xpt
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.so nphelix.so
  sudo mv /usr/lib/totem/gstreamer/libtotem-complex-plugin.so ~/.

(Note that the original plugin is copied to your home folder so you can reinstall it in the future, if you wish.)

Open Firefox and type about: plugins (without the space) in the address bar. Scroll down and look for the following entry.

  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
  File name: /opt/real/RealPlayer/mozilla/nphelix.so
  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.4005 built with gcc 3.4.3 on Feb 25 2008

If found, your Real Plugin is installed properly!


ok great, how do I uninstall this it's not working and i think it's interfering with other plugins

---

### Post by fosix on 2008-10-31
my experience for installing realplayer is to install .deb file using deb file install software. You do not need to download, after clicking the deb file for download, in the pop-up window, choose the first option not 'save to the disk', I don't remember the concret name for that option, but it is telling you to use deb install software to install.

---

