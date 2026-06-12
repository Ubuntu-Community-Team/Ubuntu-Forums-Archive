---
title: "No Red signal for Nvidia Component Out"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by schandor on 2007-05-21
Hi all,
I have an Nvidia 6600 hooked up to my TV via the component output.  When I boot the system I can see the Ubuntu splash screen just fine.  However, when I get to the GUI sign in, suddenly there is no Red signal (everything is very blue).  If I use the DVI output, everything looks fine on an LCD.  I believe I am using the nv driver in the standard repositories, but since I'm  bit new to Ubuntu, I can't swear by that statement.

Anyone out there have any thoughts?

Thank you in advanced.

---

### Post by schandor on 2007-05-24
Anyone?  Anyone at all?

---

### Post by bwah on 2007-05-27
I'm right there with you on this one.  I've got a 7600GT and it's been an ongoing issue with me that I've never seen anybody else even mention.  I've tried kubuntu and knoppmyth and both have a horrible blue cast to the GUI once the nvidia driver loads.  BIOS and everything prior to the driver loading looks fine- colors are correct, etc. so I think we can safely rule out hardware problems.

I've tried different flavors of drivers, all to no avail.  Given my recent relocation, I'm not able to run my mythtv box to my LCD monitor any longer (on which the colors were displayed properly).  I'm forced to try and get the TV out working with the correct colors.  

Any help would be greatly appreciated!

Bwah

---

### Post by moeFinley on 2007-05-27
I'm running a NVidia card connected to a TV and a monitor.

By default my setup will only display the login screen on the main monitor, so you're just seeing a clone of Ubuntu splash screen until then.  I'm not sure if this can change?  But maybe setting up auto login would be a quick fix? :confused:

:edit: sorry, re-read your question.  Ignore me.

Here's another thought instead.  Composite pipes all the colours through one connection, S-Video uses three separate signal (red, blue, green).  Could you have something set to conflicting settings so it's trying to pipe composite through an S-Video connection?

---

### Post by schandor on 2007-05-28
Hi all,
I figured out the fix...kinda.  I've since formatted the drive as I wanted to start clean.  Since I'm doing this from memory, you may need to double check the syntax on other forums.  Here's what I did:
1) Navigate to the directory that contains your xorg.conf file
2) Backup the file ([FONT="Courier New"]sudo cp xorg.conf xorg.conf.old[/FONT])
3) Use nano to open the file to edit. ([FONT="Courier New"]sudo nano xorg.conf[/FONT])
4) Navigate down the file to a section called "Device"
This is where is gets interesting/memory get's slightly fuzzy.
In the "device" section, add a line:
[FONT="Courier New"]Option     "StandardTVOut"     "HD1080i"[/FONT]

I also had to add a resolution option for 1920x1080 in a section I don't remember.

Again, you'll need to comb the forums to verify the syntax, but I hope this point you in the right direction.

---

### Post by bwah on 2007-05-28
Thanks for the replies all.  I'm using a component (Y'PbPr) connection to a standard Def. TV.  

moeFinley, I think you'd be onto something but everything looks correct- colors, etc. right until the nVidia drivers kick in.  Then it's all got a blue hue to everything.  From my limited experience, that points to a software, no?

The display looks correct other than colors however, so schandor- shouldn't that be all I'd need to worry about (especially on a standard-def TV)?

bwah

---

### Post by moeFinley on 2007-05-28
> **bwah said:**
> 
moeFinley, I think you'd be onto something but everything looks correct- colors, etc. right until the nVidia drivers kick in.  Then it's all got a blue hue to everything.  From my limited experience, that points to a software, no?


The NVidia driver can switch it's output between s-video and composite so it could still be software.  As the driver loads it changes the setting or something?

---

### Post by dantrevino on 2007-08-19
If yall are still having issues, take a look here:
[http://www.mythtv.org/wiki/index.php/ComponentOut](http://www.mythtv.org/wiki/index.php/ComponentOut)

---

### Post by Brian96 on 2008-06-21
> **bwah said:**
> Thanks for the replies all.  I'm using a component (Y'PbPr) connection to a standard Def. TV.  

moeFinley, I think you'd be onto something but everything looks correct- colors, etc. right until the nVidia drivers kick in.  Then it's all got a blue hue to everything.  From my limited experience, that points to a software, no?

The display looks correct other than colors however, so schandor- shouldn't that be all I'd need to worry about (especially on a standard-def TV)?

bwah

I see this thread has died, but did you ever get this worked out?

I'm having the same problem in Hardy.

---

