---
title: "Xorg.conf screws up when trying to modify"
date: 2009-08-13
forum: Multimedia Software
---

### Post by Theory5 on 2009-08-13
My xorg.conf file wont allow me to modify anything. I am trying to make my TX2-1270us tablet PC fully functional, but I cant get it too work, and I have no Idea how to actually modify my xorg.conf file. Each time I try something from these howto forum posts, it doesnt work.It screws up my xorg file and I need to restore from backup. Any help?
these are some of the sites:
[http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)
[http://ubuntuforums.org/showthread.php?t=1038898](http://ubuntuforums.org/showthread.php?t=1038898)

---

### Post by Favux on 2009-08-13
Hi Theory5,

You have the HP TX2z (touchsmart), correct?  Could you tell me what version of Ubuntu you are using.  Jaunty (9.04) or whatever.  Have you done anything else, installed linuxwacom or Ayuthia's kernel deb.s?  Could you post your current working xorg.conf.  Also do you have Vista or Win 7 installed?

---

### Post by Theory5 on 2009-08-14
> **Favux said:**
> Hi Theory5,

You have the HP TX2z (touchsmart), correct?  Could you tell me what version of Ubuntu you are using.  Jaunty (9.04) or whatever.  Have you done anything else, installed linuxwacom or Ayuthia's kernel deb.s?  Could you post your current working xorg.conf.  Also do you have Vista or Win 7 installed?

No, I dont have a TX2z, I have a TX2-1270us. Apperently it is an older model because I found its not widely know and HP doesnt even have it in their list of TX2 laptops anymore. But its good, and I like it. Your posts are the only ones I can find that have anything to do with the HP tablet laptops. 
The wierd thing is, that I was going to install those kernal debs, but when I ran them apperently they were already installed. My current working xorg.conf file is the basic one, I will post it later. Its pretty short.
I have vista installed 64-bit, and 64-bit Jaunty. Im Dual booting for the moment.

---

### Post by Favux on 2009-08-14
Hi Theory5,

Are you sure?  How old is it (when did you get it?)?  Is this your notebook?:  [http://www.shopping.hp.com/product/computers/notebooks/tx2z_series/rts/3/storefronts/NV174UA%2523ABA](http://www.shopping.hp.com/product/computers/notebooks/tx2z_series/rts/3/storefronts/NV174UA%2523ABA)  If not can you show me a site that displays it?

Edit:  One quick way to tell is that the TX2z does not have an "eraser".  A button on the back of the stylus where an eraser would be that retracts into the stylus barrel when you press it.

---

### Post by Theory5 on 2009-08-14
Yes, thats my exact laptop. Hmm thats wierd that HP is still selling it. I got it from newegg a month or two ago. I couldnt find it under HP's driver search thats why I thought it was older. And yes I dont have an eraser on my stylus.

---

### Post by Favux on 2009-08-14
Hi Theory5,

OK, so here's what's going on.

HP TX1000  touchscreen Nvidia  graphics?  uses evtouch drivers
HP TX2000  Wacom digitizer & touchscreen Nvidia  graphics  uses linuxwacom drivers
HP TX2500  Wacom digitizer & touchscreen ATI graphics  uses linuxwacom drivers
HP TX2z    N-trig digitizer (built in touch)  ATI graphics  can use linuxwacom drivers (if appropriate modifications are made)

HP originally called it the TX2z then changed the name to TX2-whatever.  So for short we call the series the TX2z's.  Because it uses the N-trig digitizer things are different.  HP also adds Touchsmart or multitouch to the description.

With the N-trig digitizer you can't use linuxwacom straight.  In Intrepid there is a patch to the linuxwacom drivers so N-trig will work with them.  In Jaunty most of the patches are to the kernel and then you can use linuxwacom.  Rafi Rubin has been submitting N-trig patches to the HID section of the usb kernel drivers for the last few kernels.  So now with 2.6.31 n-trig stuff almost works out of the box.  That's the kernel Kharmic will have.

So you want to look at Appendix 2 here:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)  And install Ayuthia's latest kernel deb.s.  He's fixed some stuff and N-trig works better.  The deb.s contain all of Rafi's kernel patches.  Then you want to install the attached xorg.conf.  Also you want to comment out the n-trig section of the 10-wacom.fdi.

This all assumes you have the default 0.8.2-2 linuxwacom packages that come with Jaunty installed.  You can check in Synaptic Package Manager and see if 0.8.2-2 wacom-tools & xserver-xorg-input-wacom are installed.  If you have tried to install other linuxwacom versions we may have some difficulties.  We may have to clean things up a bit.

So ask if you have questions.

---

### Post by Theory5 on 2009-08-18
Yes, I looked under apendix 2 and the first time that i had a problem with xorg.conf was when I added that 
```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"touch"		"SendCoreEvents"
EndSection

```

I will try adding the xorg.conf file that is attached, I hope it works.
And apperently I already have the .deb packages you want me to download, because when I run them the only option is for me to reinstall them.

---

### Post by Favux on 2009-08-18
Hi Theory5,

It should because you have the Vista firmware.  The alternative would be:
```
Section "ServerLayout"
	Identifier	"X.org Configured"
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"touch"		"SendCoreEvents"
EndSection
```
Also if you do not have the default Jaunty 0.8.2-2 linuxwacom installed there may be a problem.  You haven't installed a different version of linuxwacom have you?

And remember you will need to comment out the n-trig section of the 10-wacom.fdi.

---

### Post by Theory5 on 2009-08-21
> **Favux said:**
> Hi Theory5,

It should because you have the Vista firmware.  The alternative would be:
```
Section "ServerLayout"
	Identifier	"X.org Configured"
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"touch"		"SendCoreEvents"
EndSection
```
Also if you do not have the default Jaunty 0.8.2-2 linuxwacom installed there may be a problem.  You haven't installed a different version of linuxwacom have you?

And remember you will need to comment out the n-trig section of the 10-wacom.fdi.

Where is the tutorial for commenting out the n-trig section of 10-wacom.fdi
and why would I want to do that? My computer use n-trig...

I fixed the xorg.conf problem. But I dont understan why it crashes my xorg.conf each time I try to edit my xorg.conf file.

sorry for all the edits, but another thing is I just received updates and it upgraded my kernal to .15 from .14 
Does that pose problems?

---

### Post by Favux on 2009-08-21
Hi Theory5,

Yes, updating the kernel does cause a problem.  Remember you are using a modified kernel from the deb.'s.  So if you want to use the newer kernel you have to either patch it yourself following Ayuthia's patching HOW TO or wait for him to do it and put it in new kernel deb.s.

You comment out the .fdi because you are using xorg.conf not the wacom.fdi to configure your TX2z.  Theoretically it shouldn't matter but practically we found the n-trig subsection of the wacom.fdi does interfere with touch.

To comment out the n-trig subsection of the '10-wacom.fdi' at '/usr/share/hal/fdi/policy/20thirdparty/' do this.  The n-trig part looks like this:
```
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
  </device>
```
Notice the section label, N-Trig Duosense etc., is bracketed by <!--  -->.  Those are the .fdi versions of comments.  Move the trailing one to after the match line where I show below:
```
    <!-- N-Trig Duosense Electromagnetic Digitizer
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match> -->
  </device>
```
Do not get the </device>, that isn't part of the section.  I just left it in to show you the trailing comment goes after the </match> and before the device.  Then reboot.

To edit it use:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi
```

I don't know why working with the xorg.conf is crashing X.  When Jaunty first came out adding "ServerLayout" especially with wacom entries would crash X for some people.  There wasn't a pattern I could see.  But it turned out to be a bug in Xserver and they fixed it in an update.  At least I'm pretty sure they did because the problem went away.  So one thought I had is maybe it's the .fdi.  Doesn't seem likely, but you need to comment it out anyway to get touch working right through xorg.conf.

So that leaves a video problem or a firmware problem.  If you are using the video sections from your working xorg.conf you should be OK.  The other thing is that there is a firmware change to n-trig between Vista and Win7.  This changes the usb by-path line in the stylus and touch sections.  If you try to use the wrong by-path for your firmware it will also crash X.

Hope this sheds some light.

---

### Post by Theory5 on 2009-08-21
[http://linuxfans.keryxproject.org/?page_id=6](http://linuxfans.keryxproject.org/?page_id=6) 
this is the howto for me to compile it with the latest version?

---

### Post by Favux on 2009-08-21
Hi Theory5,

Yes that's Ayuthia's n-trig patching HOW TO.

---

### Post by Theory5 on 2009-08-21
> **Favux said:**
> Hi Theory5,

Yes that's Ayuthia's n-trig patching HOW TO.

ok and I just replace the 
```

sudo dpkg -i linux-image-2.6.28-14-generic_2.6.28-14.47_amd64.deb
sudo dpkg -i linux-headers-2.6.28-14-generic_2.6.28-14.47_amd64.deb

```

with my current version?

---

### Post by Favux on 2009-08-21
Hi Theory5,

Right.  Of course your deb.s will be labeled with the current kernel version you are using 2.6.28-15.?? I guess.

---

### Post by Theory5 on 2009-08-21
well I found atleast one problem. I didnt have the 0.8.2-2 linuxwacom installed, just the other one. SO that might help with some of these problems. and after compiling these packages, I will edit the 10-wacom.fdi

---

### Post by Favux on 2009-08-21
Hi Theory5,

> I didnt have the 0.8.2-2 linuxwacom installed, just the other one.
Not sure what you mean.  You should have the two default Jaunty 0.8.2-2 linuxwacom packages, xserver-xorg-input-wacom & wacom-tools, in Synaptic Package Manager installed for this to work.

---

### Post by Theory5 on 2009-08-21
ok so I did everything, and I commented out the section you said to comment out, and now touch works but when I use my stylus or my finger, the pointer doesnt jump to it, how do I fix this?
sorry, I meant that I only had the xserver-xorg-input-wacom  package installed at first.

---

### Post by Favux on 2009-08-21
Wow you patched and installed the new kernel that quickly?  N-trig part of the .fdi commented out.  Is the  xorg.conf now installing OK?

> and now touch works but when I use my stylus or my finger, the pointer doesnt jump to it, how do I fix this?
I don't understand.  What do you mean touch is working?  The cursor responds?  But the cursor isn't under the stylus and your finger?

---

### Post by Theory5 on 2009-08-21
> **Favux said:**
> Wow you patched and installed the new kernel that quickly?  N-trig part of the .fdi commented out.  Is the  xorg.conf now installing OK?

Im going to try that now.
> 
I don't understand.  What do you mean touch is working?  The cursor responds?  But the cursor isn't under the stylus and your finger?
sorry, I mean 
"and now touching the screen with my finger works, before it only worked with the stylus. But when I use either my stylus or my finger on the tablet, the pointer doesnt jump to it, how do I fix this?"

---

### Post by Favux on 2009-08-21
Well if you haven't installed the xorg.conf you don't have the calibration coordinates.  Is that what you're saying?

---

### Post by Theory5 on 2009-08-21
Yup, it works, but Im still having problems with the cursor not jumping to my finger or stylus.

---

### Post by Favux on 2009-08-21
Ok

You've patched the new kernel with Rafi Rubin's n-trig patches per Ayuthia's HOW TO, generated the deb.s and installed them.

You've installed the xorg.conf.

You've commented out the n-trig section in the 10-wacom.fdi.

And rebooted.

Could you show me your xorg.conf?  And do you have Vista firmware?

---

### Post by Theory5 on 2009-08-21
> **Favux said:**
> Ok

You've patched the new kernel with Rafi Rubin's n-trig patches per Ayuthia's HOW TO, generated the deb.s and installed them.

You've installed the xorg.conf.

You've commented out the n-trig section in the 10-wacom.fdi.

And rebooted.

Could you show me your xorg.conf?  And do you have Vista firmware?
Yup that sounds about right.
here is the xorg.conf file
and I do have vista firmware.

---

### Post by Favux on 2009-08-21
Alright.  Let's try just the stylus and touch sections first without "ServerLayout".  This assumes you have the TX2z with Vista firmware and have never tried Win7 on your TX2z.

To edit xorg.conf use:
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Theory5 on 2009-08-21
> **Favux said:**
> Alright.  Let's try just the stylus and touch sections first without "ServerLayout".  This assumes you have the TX2z with Vista firmware and have never tried Win7 on your TX2z.

To edit xorg.conf use:
```
gksudo gedit /etc/X11/xorg.conf
```

ok, every seems to be working fine, except for the cursor not jumping to my stylus or finger.

---

### Post by Favux on 2009-08-21
Hi Theory5,

That's to be expected.  We're adding stuff step wise to try an isolate the problem, if it occurs.

So now let's add "ServerLayout" but leave the wacom entries inactive (commmented out).

---

### Post by Theory5 on 2009-08-21
> **Favux said:**
> Hi Theory5,

That's to be expected.  We're adding stuff step wise to try an isolate the problem, if it occurs.

So now let's add "ServerLayout" but leave the wacom entries inactive (commmented out).

ok that works to.

---

### Post by Favux on 2009-08-21
Hi Theory5,

OK, we're getting to the point if there's going to be X breakage this will do it.  So be ready to restore the last working xorg.conf from backup at the command line.

Now let's activate the wacom entries in "ServerLayout" but keep the "SendCoreEvents" inactive.  So change "ServerLayout" to look like this:
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
#	Identifier	"X.org Configured"	# New for Jaunty?
	InputDevice	"stylus"	#"SendCoreEvents"
	InputDevice	"touch"		#"SendCoreEvents"
EndSection
```
Then reboot.

---

### Post by Theory5 on 2009-08-21
> **Favux said:**
> Hi Theory5,

OK, we're getting to the point if there's going to be X breakage this will do it.  So be ready to restore the last working xorg.conf from backup at the command line.

Now let's activate the wacom entries in "ServerLayout" but keep the "SendCoreEvents" inactive.  So change "ServerLayout" to look like this:
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
#	Identifier	"X.org Configured"	# New for Jaunty?
	InputDevice	"stylus"	#"SendCoreEvents"
	InputDevice	"touch"		#"SendCoreEvents"
EndSection
```
Then reboot.

sweet, everything is working now. Not sure why, but it is. and the cursor jumps to my finger or stylus now. 
Now to go and read the stuff on getting the bezel buttons to work and rotating the screen. Thanks a bunch, favux.

---

### Post by Favux on 2009-08-21
Hi Theory5,

Outstanding!  You're welcome.

I'm not sure how "stable" it is without the "SendCoreEvents" active.  You could try the final step of removing the comments in front of them.  That would be proper "Wacom" syntax.  Of course that could be what was breaking X for you.  But I think worth a try.

---

### Post by Theory5 on 2009-08-21
oh, on your rotation thread, which parts are made for TX2z rotation? You said to look at apendix 2 but it doesnt mention anything about rotation.

---

### Post by Favux on 2009-08-21
Hi Theory5,

Method 1 or 3 should work for you.

And towards the bottom in big bold Auto-Magic Rotation has links to the script in post #225:  [http://ubuntuforums.org/showthread.php?t=996830&page=23](http://ubuntuforums.org/showthread.php?t=996830&page=23)  Or the current version of Red_Lion's rotation applet in post #272:  [http://ubuntuforums.org/showthread.php?t=996830&page=28](http://ubuntuforums.org/showthread.php?t=996830&page=28) which works for Ayuthia on his TX2z.

---

### Post by R3fr4cti0n on 2009-08-24
> **Theory5 said:**
> ok so I did everything, and I commented out the section you said to comment out, and now touch works but when I use my stylus or my finger, the pointer doesnt jump to it, how do I fix this?
sorry, I meant that I only had the xserver-xorg-input-wacom  package installed at first.

Theory5 what exactly did you do and in what order to get this to work, Fauvx and i have 6 pages of forum on this same problem so if you could jump me ahead that would be great!

---

