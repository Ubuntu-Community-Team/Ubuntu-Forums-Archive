---
title: "Ubuntu 8.04 &amp; Flash"
date: 2008-10-18
forum: Multimedia Software
---

### Post by kcyanks1 on 2008-10-18
When I try and stream a flash video, it generally works for a few minutes.  Then it starts getting choppy and slows my computer to a crawl.  If I can even manage to get out of Firefox (generally by force closing the misbehaving app), my computer remains very slow for everything else I may try to do.  I sometimes have to even reboot/shutdown twice before it works properly again.  I'm currently using the flashplugin-nonfreebeta package version rc10.0.10.12; I also previously had been using flashplugin-nonfree version 9 (9.0124.0 I think), and I had the same problem (that's why I tried the beta version).  I believe at one point I also tried the free flash plugin (which I'd prefer to use in principle), but then I think some videos wouldn't play at all.

Some other specs:
Firefox 3.0.3
Dell Latitude D620
nonfree nvidia video driver

If anyone has any ideas, it would be greatly appreciated.  Thanks!

---

### Post by wolfen69 on 2008-10-18
have you tried the final version of flash 10? make sure to remove older versions first.

---

### Post by gjoellee on 2008-10-18
Read about and download flash here: [http://www.kshoster.net/node/52](http://www.kshoster.net/node/52) (don't worry it is .deb (it means double click on the downloaded package and let it install))

---

### Post by kcyanks1 on 2008-10-18
> **gjoellee said:**
> Read about and download flash here: [http://www.kshoster.net/node/52](http://www.kshoster.net/node/52) (don't worry it is .deb (it means double click on the downloaded package and let it install))


Thanks to both of you for the relies.  I removed my current version (through Synaptec) and then installed the package from the .deb file at the link quoted above.   Same problem occurred.  Maybe a little more detail on what exactly I see/hear would help.  The first step is generally the audio going on normally and the video getting all choppy and falling behind.  Then the audio gets all messed up too.  The latest time I had maybe around 5 minutes of OK watching before major problems started.  Thanks again.

---

### Post by kcyanks1 on 2008-10-18
I just tried using Firefox 2 (which still is installed even though I use 3.0.3) and Konquerer.  Same problem ocurred with the other browsers, so it shouldn't be a FF3 issue.  This has been happening for a while but not forever--since FF3 is not the issue, it might actually have started when I upgraded from 7.10 to 8.04.

---

### Post by kcyanks1 on 2008-10-18
Also just tried changing my settings in System->Preferences->Sound to use "ALSA" instead of "Autodetect" in case the problem was PulseAudio. At the same time I removed mplayer, since I never use it, and I did some additional google searching and someone I think suggested that (even though I'm not sure why it should matter).  I realize multiple changes at once isn't the best diagnostical method...in any case, it didn't solve the problem.  Maybe the next step is using "PulseAudio" or something else instead of "ALSA" or "Autodetect"?  Thanks again, and sorry for mass posting.

---

### Post by brettnak on 2008-10-19
Have you tried the newest version of flash player 10?  The final version?

Try this:


1) Uninstall the beta:
```
sudo apt-get remove flashplugin-nonfreebeta
```
2) Download the new version:
```
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
```
3) Decompress it:
```
tar xvf install_flash_player_10_linux.tar.gz
```
4) Install it:
```
cd install_flash_player_10_linux; ./flashplayer*
```

It will say something about not installing for all users, just say okay or yes.  This just means it will install to ~/.mozilla, there's nothing wrong with that unless you have multiple users on your machine.

Alternatively, if you still want to use packages, remove the beta flash player, and install the new one from the deb package. ie.

```
sudo apt-get remove flashplugin-nonfreebeta
```

Then visit [_[COLOR="DeepSkyBlue"]Adobe's Download Site[/COLOR]_]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux") and download the ".deb" (debian or ubuntu, depending on how adobe feels about .deb packages on this particular day) installer.  Double click on it to install the package.  If you decide to remove the package later, do:

```
sudo apt-get remove adobe-flashplugin
```

---

### Post by gandaran on 2008-10-19
try this, right click the flash video window, disable the hardware acceleration option

---

### Post by kcyanks1 on 2008-10-19
> **brettnak said:**
> Have you tried the newest version of flash player 10?  The final version?


I believe so -- I followed the instructions from the second poster above and installed the .deb file from the link he provided ([http://www.kshoster.net/node/52](http://www.kshoster.net/node/52)).  It was definitely a more recent version than the beta version I had been using.

Edit:  Yes, I am.  I have version 10.0.12.36 installed, which is the latest version from Adobe's website.

> **gandaran said:**
> try this, right click the flash video window, disable the hardware acceleration option

This seems to be working!  I will have to give it more time and tests, but I've had a video running longer than I can recall having done recently.  I'll give an update after I've had more chances to test it, but thanks!

---

### Post by jwhiz on 2008-10-20
Hi;
I read the previous postings with interest. 
I can't seem to get any flash player working at all.
The FF3 addons shows Shockwave flash 10.x(latest) and Gnash and Totem...but nothing happening at YouTube, etc.
I did the apt-get thing for the shockwave player, and as I said, all these players are showing up. I also seem to have some version of Windows Media Player as the default for a lot of streaming/downloading media.
Bwuh?
I haven't set the media defaults myself, should I change any of these?
And what did yo mean by the video player window for the hardware acceleration? (I'm not even getting a video player window on sites, although something like it flashes for a split second when leaving the main site window!)
This is a new one on me, I haven't had any Flash issues on any of the 3 platforms, anytime I've had the option to update, that's worked. Not this time!

---

### Post by kcyanks1 on 2008-10-21
> **jwhiz said:**
> Hi;
I read the previous postings with interest. 
I can't seem to get any flash player working at all.
The FF3 addons shows Shockwave flash 10.x(latest) and Gnash and Totem...but nothing happening at YouTube, etc.
I did the apt-get thing for the shockwave player, and as I said, all these players are showing up. I also seem to have some version of Windows Media Player as the default for a lot of streaming/downloading media.
Bwuh?
I haven't set the media defaults myself, should I change any of these?
And what did yo mean by the video player window for the hardware acceleration? (I'm not even getting a video player window on sites, although something like it flashes for a split second when leaving the main site window!)
This is a new one on me, I haven't had any Flash issues on any of the 3 platforms, anytime I've had the option to update, that's worked. Not this time!

As I was the one who had the problem here, who knows if I can help, but if you can clarify things it might help me or someone else help you.

(1) You installed Flash, not Shockwave, right?  They are different things, I believe.

(2) By FF3 "addons," do you mean going to Tools->Add-ons?  Flash shouldn't be there.

Edit (this line):  (3) Can you run "dpkg -l | grep flash" and post the results?

Thanks.

---

### Post by gandaran on 2008-10-21
> **jwhiz said:**
> Hi;
I read the previous postings with interest. 
I can't seem to get any flash player working at all.
The FF3 addons shows Shockwave flash 10.x(latest) and Gnash and Totem...but nothing happening at YouTube, etc.
I did the apt-get thing for the shockwave player, and as I said, all these players are showing up. I also seem to have some version of Windows Media Player as the default for a lot of streaming/downloading media.
Bwuh?
I haven't set the media defaults myself, should I change any of these?
And what did yo mean by the video player window for the hardware acceleration? (I'm not even getting a video player window on sites, although something like it flashes for a split second when leaving the main site window!)
This is a new one on me, I haven't had any Flash issues on any of the 3 platforms, anytime I've had the option to update, that's worked. Not this time!
you shouldn't have gnash installed! just adobe flash, that's what causing your problem

---

### Post by jwhiz on 2008-10-26
> **kcyanks1 said:**
> As I was the one who had the problem here, who knows if I can help, but if you can clarify things it might help me or someone else help you.

(1) You installed Flash, not Shockwave, right?  They are different things, I believe.

(2) By FF3 "addons," do you mean going to Tools->Add-ons?  Flash shouldn't be there.

Edit (this line):  (3) Can you run "dpkg -l | grep flash" and post the results?

Thanks.

3 - 
ii  flashplugin-nonfree                        9.0.124.0ubuntu2                         Adobe Flash Player plugin installer


Does this mean I still have an older version of Adobe Flash player, which should have been removed? Yeesh.
I was referring to all the media players, including shockwave flash player.

---

### Post by jwhiz on 2008-10-26
> **gandaran said:**
> you shouldn't have gnash installed! just adobe flash, that's what causing your problem

Thanks, I wondered about conflict, I'll try disabling gnash and see what happens.

and - how does the subscribed threads work here? (usually automatic in other forums!)

---

### Post by kcyanks1 on 2008-10-26
> **jwhiz said:**
> 3 - 
ii  flashplugin-nonfree                        9.0.124.0ubuntu2                         Adobe Flash Player plugin installer


Does this mean I still have an older version of Adobe Flash player, which should have been removed? Yeesh.
I was referring to all the media players, including shockwave flash player.

That is an old version.  If you follow some of the instructions earlier in the thread that others gave me, you will be able to get the latest version.  But I actually think the normal Ubuntu (nonfree) repositories have the latest version, so you should be able to use Synaptec and normal repos rather than going directly to Adobe's website.  Do you regularly install updates when asked?  Also, did you originally install flash through Synaptec (or apt-get if you use the console)?

---

