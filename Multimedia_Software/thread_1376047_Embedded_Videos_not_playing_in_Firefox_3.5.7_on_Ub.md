---
title: "Embedded Videos not playing in Firefox 3.5.7 on Ubuntu 9.10"
date: 2010-01-08
forum: Multimedia Software
---

### Post by macsdev on 2010-01-08
Hi,

I am not able to play Youtube videos whenever it's embedded in pages other than the Youtube.com pages. But it play just about fine on the original page. Any one else facing the same problem?

I'm new to this forum. Bear with me if I have not posted correctly :)

---

### Post by RedSingularity on 2010-01-08
You did install the flash player right?

---

### Post by macsdev on 2010-01-08
I did install the Flash Player plugin when I first went to the Youtube website after installing Ubuntu.

---

### Post by RedSingularity on 2010-01-08
What if you do this in a terminal 

sudo apt-get install flashplugin-installer

---

### Post by macsdev on 2010-01-08
This is the output for the command.
> 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



Let me get one thing clear, the problem is not with the videos in the actual Youtube website. They play just fine. But whenever it's embedded in some other website, they just don't play. It's like they have a big play button inside the actual play screen and when I click on them, nothing happens.

---

### Post by RedSingularity on 2010-01-08
Do you have Java installed?  If it is a java app then flash wont play it.

---

### Post by misterglitch on 2010-01-08
I had the same problem, too.  I fixed it by rolling back to an older version of Flash than the one installed by flashplugin_installer.  The version I used was 10.0 r32.  You can rollback by uninstalling flashplugin_installer and then manually installing the older version with the following code.

```

sudo apt-get remove flashplugin-installer flashplugin-nonfree 
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins/

```

Hope that helps.

---

### Post by macsdev on 2010-01-08
@RedSingularity

I don't think I have Java installed. Atleast, Synaptic says so.

@misterglitch

Now I have a new problem. After executing the commands, now firefox is crashing when I open a page with embedded videos. :(

Oh my, it's crashing when I open my Gmail account also, consistently.

---

### Post by misterglitch on 2010-01-08
You can always undo the manual installation with:

```

sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm /usr/lib/firefox-addons/plugins/libflashplayer.so

```

If you're crashing without the plugin installed, the problem is presumably not with flash.

---

### Post by macsdev on 2010-01-08
I restarted my PC and it works like a charm. Thanks a ton.

I have one more question though, whenever I play a Youtube video in Fullscreen, if I try to reduce the volume by using a shortcut key on my keyboard (mine is a Dell Inspiron), the video comes out of the Fullscreen mode. Is there any work around for this?

---

### Post by GeekGirl1 on 2010-01-08
> **misterglitch said:**
> I had the same problem, too.  I fixed it by rolling back to an older version of Flash than the one installed by flashplugin_installer.  The version I used was 10.0 r32.  You can rollback by uninstalling flashplugin_installer and then manually installing the older version with the following code.

```

sudo apt-get remove flashplugin-installer flashplugin-nonfree 
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar xf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins/

```

Hope that helps.Yes, it certainly helped me. I was getting no video on youtube.com. Video and audio are now working correctly. Thank you.

Copy and paste the only first line of code into a terminal, hit enter. Then, copy and paste the rest of the lines. *apt-get remove* will stop to ask a question which breaks the pasted "script" if you try to run all the code at one time.

---

### Post by macsdev on 2010-01-15
> Whenever I play a Youtube video in Fullscreen, if I try to reduce the volume by using a shortcut key on my keyboard (mine is a Dell Inspiron), the video comes out of the Fullscreen mode. Is there any work around for this?

Bounce :)

---

### Post by macsdev on 2010-01-17
Bounce :(

---

### Post by macsdev on 2010-01-24
> **macsdev said:**
> Whenever I play a Youtube video in Fullscreen, if I try to reduce the volume by using a shortcut key on my keyboard (mine is a Dell Inspiron), the video comes out of the Fullscreen mode. Is there any work around for this?
Bounce :( :(

---

### Post by foresthill on 2010-02-07
> sudo apt-get remove flashplugin-installer flashplugin-nonfree 
wget [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)
tar xf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
sudo cp libflashplayer.so /usr/lib/firefox-addons/plugins/

I ran this command today on my 64 bit 9.10 system and it completely hosed it. Firefox now crashes when I try to load any webpage with flash content, and even some without flash content.

Part of the problem may be that I lost my connection halfway through downloading the previous flash player version (my wireless modem hung up) after uninstalling the old one. Trying to run the install command brings up "unexpected end" errors. So I ran the uninstall command and then the install, but I got the same error message.  

I tried running the commands several times but they would not work. I thought maybe it was because I did not have sudo privileges so I closed the terminal and tried to run sudo and the terminal claimed my password was incorrect. 

I rebooted and tried to run them again and I got a message saying "remove" would not work and that I should try "autoremove" when uninstalling the flash player, but this took uninstalled the flash player along with my new kernel and a whole bunch of other stuff.

What a mess. Looks like reinstall time for me. I am used to running commands but I have never seen anything like this happen before.

So heads up trying this. Use caution. Maybe use the Synaptics Package Manager to downgrade instead, unless you want to end up like me.

---

