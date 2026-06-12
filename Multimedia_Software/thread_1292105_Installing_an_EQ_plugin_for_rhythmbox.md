---
title: "Installing an EQ plugin for rhythmbox"
date: 2009-10-15
forum: Multimedia Software
---

### Post by IAmNoodle on 2009-10-15
I love messing with the EQ on any music player I use, but Rhythmbox doesn't seem to have one. A bit of searching has found me a 10 band EQ, but can't seem to fathom the terminal commands to install it, and the guide is a bit wolly with goodle translator...

[http://www.deviantdark.altervista.org/?p=438](http://www.deviantdark.altervista.org/?p=438)

Can anyone help?

---

### Post by ajgreeny on 2009-10-15
Can't help with translation, but have a look at this which is the plain text file from my plugin, and shows a web address at the bottom.

It does work, but not too brilliantly, unfortunately, and occasionally crashes R'Box.

[RB Plugin]
Loader=python
Module=equalizer
IAge=1
Name=Equalizer
Description=10 Band Equalizer
Authors=Teemu Kallio [email]teemu.kallio@cs.helsinki.fi[/email]
Copyright=Copyright © 2008 Teemu Kallio
Website=http://cs.helsinki.fi/teemu.kallio/

From the web address at the bottom I thought you could get info, but you will just get a "Fail" image, so go to [http://jorge.fbarr.net/2009/06/30/rhythmbox-equalizer/](http://jorge.fbarr.net/2009/06/30/rhythmbox-equalizer/) instead and you will find all you need including instructions on unpacking and using.

---

### Post by IAmNoodle on 2009-10-15
Thank you for that link. I did follow the instructions given, but the terminal spat out the following

```
will@will-desktop:~$ wget http://jorge.fbarr.net/files/rhythmbox-eq.tar.gz
--2009-10-15 19:25:51--  http://jorge.fbarr.net/files/rhythmbox-eq.tar.gz
Resolving jorge.fbarr.net... 87.238.45.175
Connecting to jorge.fbarr.net|87.238.45.175|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3404 (3.3K) [application/octet-stream]
Saving to: `rhythmbox-eq.tar.gz'

100%[======================================>] 3,404       --.-K/s   in 0.07s   

2009-10-15 19:25:51 (50.0 KB/s) - `rhythmbox-eq.tar.gz' saved [3404/3404]

will@will-desktop:~$ mkdir -p ~/.gnome2/rhythmbox/plugins/
will@will-desktop:~$ tar -zxvf equalizer.tar.gz -C ~/.gnome2/rhythmbox/plugins/
tar: equalizer.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

It didn't add the eq onto the list of plug ins on RBox

Bear in mind I know practically nothing about how the terminal works, so if there's something I need to change, I wouldn't really know unless I was told

---

### Post by ajgreeny on 2009-10-15
I think that is because the name of the downloaded file has changed from what the instructions tell you.  Just change the command 
tar -zxvf equalizer.tar.gz -C ~/.gnome2/rhythmbox/plugins/
to 
tar -zxvf rhythmbox.eq.tar.gz -C ~/.gnome2/rhythmbox/plugins/
and it should work.

I think when I did it I simply made the plugin folder in nautilus and used archive manager to extract the Equalizer folder to that manually.
Both ways should work OK.

---

### Post by IAmNoodle on 2009-10-15
Sorted. Thanks for your help. I did need to change it to what you said.

I ended up having find the equalisation folder that the terminal had unpacked, copy that, get explorer (or whatever it's called. I'm used to Windows terminology) to show hidden files, find .gnome2, find rhythmbox, go into plugins and paste the equaliser folder in there. 

Rebooted rhythmbox and found it in the plug-ins

---

### Post by AdamantForce on 2009-10-22
Hello,
  I would just like to say thank you for the posted walk through. I would not have been able to figure it out on my own.  (Code and I dont mix) But I just wanted to post to avoid any future install troubles. The fix you suggested for the failed install makes perfect sense. 
But "I" being a "code noob" overlooked one tiny and crucial thing.  This is the correct line of code. Less one period, plus one dash.

   Cheers!

tar -zxvf rhythmbox-eq.tar.gz -C ~/.gnome2/rhythmbox/plugins/

:guitar:

---

### Post by AdamantForce on 2009-10-23
[attach]132789[/attach]

Screen shot provided just to make it alil easier to understand.
Ciao,
AdamantF

---

### Post by jensbodal on 2009-11-20
Sorry to bring up an old thread but I found this while searching for a Rythmbox EQ plugin, and the solution I found seems much much much easier than the one in this thread.  The directions to install can be found here: [http://cornerofseven.com/blog/2009/07/rhythmbox-eq-update/](http://cornerofseven.com/blog/2009/07/rhythmbox-eq-update/)

It's a very simple EQ but it does the job, and took this Linux noob less than a minute to install.

---

### Post by bikertappy on 2010-10-29
I installed this eq and it works nicely, but the installation instructions didn't work for me - I'm running 10.04 Lucid with the default Rhythmbox that came with it.

I initially followed the instructions and unzipped the plugin to .gnome2 but this didn't work.
With a little hunting I found that all the rest of the plugins were in /usr/lib/rhythmbox/plugins

So I copied the unzipped files to there using:


cd .gnome2/rhythmbox/plugins
sudo cp -r rbeq /usr/lib/rhythmbox/plugins


and entering my password when promtped.

I'm an utter noob so should anyone think this is questionable then let me know, otherwise I hope this helps someone else.

---

### Post by sjhaffner on 2010-11-20
Here is the equalizer plug-in I use: 
  
  [http://code.google.com/p/rbeq/](http://code.google.com/p/rbeq/)
  
I like this better than the one previously mentioned! 

  Hope this helps!

---

### Post by yusof125 on 2011-02-27
Here The Step By Step To Install The Rhytmbox 10 Equalizer Plugins:

1. Please download the latest Plugins of Equalizer at:

[http://code.google.com/p/rbeq/](http://code.google.com/p/rbeq/)

2. Extract all files in (folder rbeq) in your directory : 

home/(your username)/.gnome2/rhythmbox/plugins/

3. Open the terminal at:

 Applications/Accessories/Terminal

4. Type in this command:

cd .gnome2/rhythmbox/plugins
sudo cp -r rbeq /usr/lib/rhythmbox/plugins

Entering your password when prompted.

5. Now, run your Rhythmbox. Go to Menu Bar:

Edit/Plugins/

6. Configure Plugins:

Please check the box [ / ] to Enable Plugin of Rhytmbox Equalizer.

7. Go to Menu Bar: 

Tools/Set Equalizer

8. Choose your favorite tune.

Enjoy your song, lets dance around the room!

by yusof125

---

