---
title: "Tip: Configuring and Enabling TV out on Nvidia"
date: 2008-01-12
forum: Mythbuntu
---

### Post by ahood on 2008-01-12
**BACKGROUND**
I have been a mythtv user for the past two years using Knoppmyth. A few weeks ago I migrated to Mythbuntu. I love Mythbuntu's Myth Control Center and the ability to keep the system updated via Synaptec. 

Knoppmyth was great in that the recent releases of Knoppmyth automatically configured and enabled the TV out on my PVR-350 TV tuner card. After migrating to Mythbuntu, it wasn't long before I discovered that configuring/enabling TV out on the PVR-350 was not going to be as easy. 

I realized that this was an opportunity to begin understanding how to display Mythbuntu on my analog TV via the TV out on my Nvidia 6200 graphics card. This card has D-Sub, DVI, and TV out. The package included a dongle for composite video, s-video, and component. This was a great solution because although I have an analog TV now, sometime in the future I will probably upgrade to a digital/HD TV. The TV out dongle that came with the 6200 will allow me to output video (including the desktop) to an analog TV (via composite and s-video) or, later on, to a digital/HD TV via the component or DVI connector.

The only problem I had was that I did not have a good understanding of how to configure/enable the TV out on the Nvidia 6200 video card.

Below is an explanation of how I configured and enabled the TV out on the Nvidia 6200 video card, which allowed me to use the TV out dongle that game with this graphics card.

*NOTE: This post applies specifically  to the Nvidia 6200 video card, but may be useful for other Nvidia cards too. This post **DOES NOT** apply to those using ATI for video output.*

**INSTRUCTIONS**

**STEP 1.** Installed the video card (see manual that came with card).

**STEP 2.** Installed nVidia **proprietary** graphics driver

*Note: Before proceeding, be sure that the machine is connected to the Internet.*

[LIST]
[*]Click on **[COLOR="Sienna"]Settings[/COLOR]** --> **[COLOR="Sienna"]Screens and Graphics[/COLOR]**

[*]Enter the password

[*]In the windows titled **[COLOR="Sienna"]Screen and Graphics Preferences[/COLOR]**, Click on the **[COLOR="Sienna"]Graphics Card[/COLOR]** tab.

[*]Click on the **[COLOR="Sienna"]Driver[/COLOR]** drop down list

[*]Keep the default **[COLOR="Sienna"]Choose Driver By Name[/COLOR]** option and select **[COLOR="Sienna"]nvidia[/COLOR]**.

[*]Click the **[COLOR="Sienna"]OK[/COLOR]** button
[/LIST]

The driver will be downloaded and installed. Enter password when prompted.

**Log out and log back in to have the new driver take effect.**


**STEP 3.** Backup Current XORG.CONF File.

[LIST]
[*]At the desktop, click on **[COLOR="Sienna"]Applications[/COLOR]** --> **[COLOR="Sienna"]Accessories[/COLOR]** --> **[COLOR="Sienna"]Terminal[/COLOR]**.
[*]Type the following command...
> sudo cp /etc/X11/xorg.conf etc/X11/xorg.conf.backup1
[/LIST]

**STEP 3.** Create a New XORG.CONF File.

[LIST]
[*]Connect the TV out dongle to the back of the Nvidia graphics card, as well as to the analog TV (composite or s-video).
[*]Turn ON THE TV - **[COLOR="Red"]VERY IMPORTANT[/COLOR]** 
[*]Launch nvidia-settings by typing the following command...
> sudo nvidia-settings
[*]A window titled **[COLOR="Sienna"]NVIDIA X Server Settings[/COLOR]** will appear. Click on the second option in the list (left side) titled **[COLOR="Sienna"]X Server Display Configuration[/COLOR]**
*Note: Two boxes will appear on the right side titled **[COLOR="Sienna"]Monitor[/COLOR]** and **[COLOR="Sienna"]TV-Out[/COLOR]** indicating that the TV has been detected.*
[*]In the section titled **[COLOR="Sienna"]Display[/COLOR]**, click on the **[COLOR="Sienna"]Configure...[/COLOR]** button.
[*]A small window will appear titled **[COLOR="Sienna"]Configure Display Device[/COLOR]** and select the **[COLOR="Sienna"]TwinView[/COLOR]** option (third in the list) and then click on the **[COLOR="Sienna"]OK[/COLOR]** button.
[*]Back to the **[COLOR="Sienna"]NVIDIA X Server Settings[/COLOR]** window and in the **[COLOR="Sienna"]Display[/COLOR]** section, click on the **[COLOR="Sienna"]Position[/COLOR]** drop down list and select **[COLOR="Sienna"]Clone[/COLOR]**. Then, click on the **[COLOR="Sienna"]Apply[/COLOR]** button.
*Note: The desktop should now appear on the TV screen.*
[*]Still in the **[COLOR="Sienna"]NVIDIA X Server Settings[/COLOR]** window, click on the **[COLOR="Sienna"]Save to X Configuration File[/COLOR]** button.
[*]A small window will appear titled **[COLOR="Sienna"]Save X Configuration[/COLOR]**. 
[*]Change the path of the file from **[COLOR="Sienna"]/home/username/xorg.conf[/COLOR]** to **[COLOR="Sienna"]/home/username/xorg.conf.twinview[/COLOR]**
[*]Click on the **[COLOR="Sienna"]Save[/COLOR]** button.
[*]Back to the **[COLOR="Sienna"]NVIDIA X Server Settings[/COLOR]** window, click on the **[COLOR="Sienna"]Quit[/COLOR]** button.
[/LIST]

You should now be back at the terminal.


**STEP 4.** Replace XORG.CONF File with XORG.CONF.TWINVIEW

[LIST]
[*]At the terminal, type in the following command...
> sudo cp /home/username/xorg.conf.twinview /etc/X11/xorg.conf
[/LIST]

**STEP 5.** Restart X Server

[LIST]
[*]Click on **[COLOR="Sienna"]Applications[/COLOR]** --> **[COLOR="Sienna"]Quit[/COLOR]**
[*]Click on **[COLOR="Sienna"]Log Out[/COLOR]**
[/LIST]

You should now be at a login screen.

[LIST]
[*]Click on the user name in the login list
[*]Enter the password
[/LIST]

Video should appear on the TV screen AND monitor.

**[COLOR="Red"]ALL DONE!![/COLOR]**

I hope this helps others.

---

### Post by Caps18 on 2008-04-22
Thanks for posting this, it was exactly what I needed to do.

---

### Post by laga on 2008-04-22
Nice Howto!

I'm wondering why it didn't work automatically for you? I always thought that you just have to have the TV plugged in at boot and then it works?

I haven't used an Nvidia TV-Out for quite some time, though :)

---

### Post by Brian96 on 2008-06-15
Not to hi-jack, but does your card detect the TV during boot-up before setting it up like this?

My issue is this: I just installed a 7600 GT in my system. I have it connected to my TV using the supplied HDTV dongle (essentially 7-pin S-video to RGB component). For some reason I can't get anything on my TV when using the component connection (not even the BIOS screen during boot up).

However, if I plug the blue cable into the composite video on my TV I get a picture, but with no color.

I had a similar problem with another machine into which I installed a 7950 GT and was connecting with a plain 4-pin S-video cable (no color, fuzzy picture). I "fixed" it using a workaround I found elsewhere in which you short out a couple of pins with copper wire. (I don't understand why that works, but at least it works.)

I suppose I could just connect with S-video and use the workaround described above, but I'd rather connect with the component cables.

Anybody have any suggestions?

---

### Post by fatmonk on 2008-11-18
After a couple of weeks of head scratching, trashed installations and rebuilds I have a couple of tips for anyone struggling to get TV-out working on nVidia boards.

These are things that may catch you out (to do with video standard and detecting the TV input type).

They are a couple of settings that you may need to manually add to the /etc/X11/xorg.conf which cannot be set from the nvidia-settings GUI.

1) Set your TV out standard correctly according to your region. eg. for a PAL-I (like the UK and Japan) region, add the following line to xorg.conf:

```
Option "TVStandard" "PAL-I"
```

2) You may also need to tell the card whether or not you want to use composite video out or S-Video out. Th ecard is supposed to auto-detect this from the TV (!?), but may not, so hard setting it may solve issues of black screens on TVs.

```
Option "TVOutFormat" "SVIDEO"
```or```
Option "TVOutFormat" "COMPOSITE"
```

The following page has a list of some of the various options for the settings mentioned in 3 and 4. It's from the manufacturer who make the card I'm using, but it should apply to any vVidia card with TV-out capability.

[http://www.zotac.com/index.php?option=com_easyfaq&task=view&id=29&Itemid=29]("http://www.zotac.com/index.php?option=com_easyfaq&task=view&id=29&Itemid=29")

Finally,

3) In nvidia-settings make sure to set the card to synch to the TV-Out video, not any other computer display you have connected. If you synch to the computer display rather than the TV-out you may end up with the video 'tearing' with a horizontal line accross the screen, and any digital audio will drop out regularly every second or so.

Hope this helps someone avoid the headaches I've had over the last 2 weeks trying to get this sorted!

-FM

---

### Post by ratdog on 2008-12-31
Hello,
I cannot get this how-to to work for me.
I am using an asus motherboard with and integrated nvidia geForce 6150.
The board has composite, s-video and analog video outs.
I am trying to output video to an analog TV like the original poster.

When I click 'apply' in the Nvidia X Server Settings after selecting Twinview and Clone, I get this message:

The mode on X screen 0 has been set.  Would you like to keep the current settings?

But nothing at all happens.  My TV is detected in the nvidia settings, and when I restart X the TV flickers during startup indicating that the TV is getting some sort of signal.

Any Ideas?  I'm trying to get this going to add visuals to a DJ performance I'm doing this evening!

Thanks

---

### Post by enchesss on 2009-01-02
does the tv go black after flickering? (may be related to not setting up the tv out signal e.g. pal - b for australia)


or do you get the blue (no signal) screen


you say that the tv is being detected how do you know this?

is there any settings for the tv in the nvidia control panel 

e.g. can you describe the screen position.


For some reason my nvidia x server does not like to run the tv setup wizard that was located as an option in the panel on the left under display setup wizaed.

 any more - nut you may need to run this and choose pal -B australia if it gives you the option.

---

### Post by agiamba on 2009-01-05
Hi, hopefully someone can help me out.

I'm trying to output using Mythbuntu on an Nvidia card, I have the drivers installed and everything. But for some reason my TV can't output at 1024x768 resolution. I can't figure out a resolution that fits the screen, anything lower is too small. Ideas? Please PM me or respond if you can help.

---

### Post by ahood on 2009-01-06
> **ratdog said:**
> Hello,
I cannot get this how-to to work for me.
I am using an asus motherboard with and integrated nvidia geForce 6150.
The board has composite, s-video and analog video outs.
I am trying to output video to an analog TV like the original poster.

When I click 'apply' in the Nvidia X Server Settings after selecting Twinview and Clone, I get this message:

The mode on X screen 0 has been set.  Would you like to keep the current settings?

But nothing at all happens.  My TV is detected in the nvidia settings, and when I restart X the TV flickers during startup indicating that the TV is getting some sort of signal.

Any Ideas?  I'm trying to get this going to add visuals to a DJ performance I'm doing this evening!

Thanks

Hello,

Just to confirm, did you follow steps 3 and 4 above?

Do you use PAL or NTSC? If PAL, did you try the post above?

Post the content of the /etc/X11/xorg.conf file.

Al

---

### Post by pblack00 on 2009-06-11
I realize that this is a very old thread, but would love is someone could help.  I followed the directions in the for an install of Ubuntu 9.04, with an Nvidia card.  It worked well and I can now see my TV from the machine, but I seem to have caused some other problems.  Terminal will start and I have no text in it, just a white box, as well as not red X in the top right corner.  I don't know if it was these directions, or something else I did (complete Linux Noob, and it's kickin' my butt!)

Please help!
pblack00

---

### Post by pblack00 on 2009-06-15
bump

---

