---
title: "fglrx has got to be kidding me!"
date: 2009-03-30
forum: Multimedia Software
---

### Post by duru on 2009-03-30
Hi, I am sort of a newbie.

What I experience is, after having a ```
sudo dpkg-reconfigure xserver-xorg
``` and trying a ```
sudo amdcccle
``` I get the output ```
X Error: BadRequest (invalid request code or no such operation) 1
  Extension:    156 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x17
.
.
.
Parse error on line 22 of section Device in file /etc/X11/xorg.conf
	"Identifier" is not a valid keyword in this section.
Parse error on line 22 of section Device in file /etc/X11/xorg.conf
	"Identifier" is not a valid keyword in this section.
Segmentation fault

```

for which the xorg.conf is
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

And when I edit line#22 to ```
Section "Device"
EndSection
```
I get the error
```
Parse error on line 22 of section Device in file /etc/X11/xorg.conf
	"Identifier" is not a valid keyword in this section.
Parse error on line 22 of section Device in file /etc/X11/xorg.conf
	"Identifier" is not a valid keyword in this section.
Segmentation fault

```
And if delete that section completely then I get the same "Identifier" error for the next section.

If you wonder how I got to this point is, (I think) I installed ATI driver using **envyng**. Before and after this, the rendering was/is very slow and I kept getting for **glxinfo, fglrxinfo, glxgears** this output:```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  156 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

``` which made me to reconfigure the xserver-xorg as in [here]("http://ubuntuforums.org/showthread.php?t=981857") which looks solved now. Whatever, in the meantime I set up using **aticonfig** a dual screen with **Xinerama**.

Please see attached my **lspci** output and **Xorg.0.log**.

Any help may prevent me from committing suicide.
TIA
duru

---

### Post by rolandrock on 2009-03-30
Hi Duru,

It is not clear from your post what you have fixed and what is still a problem.  Your Xorg.0.log suggests dualhead does not work.  Is this true?  What other problems remain after your modifications?

There are some instructions here for installing the driver manually:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

You should uninstall the existing driver before trying to re-install.

I've attached an xorg.conf that works for me (Radeon HD2400, screen0 lcd monitor, screen1 s-video tv).  You could try merging your keyboard and mouse settings with that.  Note that composite (->Compiz) is disabled: I found that necessary to play films properly with dualhead.  I don't know how this would work with Xinerama.

If you still have problems, post the output of 'fglrxinfo -n' and glxinfo.

---

### Post by Melcar on 2009-03-30
Once you do the dpkg-reconfigure step, you pretty much ax your fglrx install (you just reconfigured X to the default settings).  You have to reinstall fglrx (or restore your xorg.conf to its fglrx configuration).

---

### Post by markbuntu on 2009-03-30
First of all, Envy does not work for most ati cards and will misinstall the driver so don't use it. The driver you have must be removed completely.

After you reinstall the driver you need to run

aticonfig --initial -f

Then you should be able to configure dual monitors with the Catalyst Control Center.

---

### Post by duru on 2009-04-01
Hi,

Thank you very much for your answers and sorry for my late reply. I was really in a bad mood because of these and sleeping the whole time.

Now after my post, I did
```
sudo aticonfig --initial=dual-head
sudo aticonfig --adapter=all --initial

```
and then I added the Xinerama manually. The xorg.conf and Xorg.0.log are attached.

The **glxinfo, fglrxinfo, glxgears** still give me
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

As far as I understand from your posts, I have never succeeded to install fglrx or something else. Now I will uninstall all (including envy) and install again according to the link you give. My version is Intrepid Server Edition 64x (sorry for not mentioning before), but [the instructions for Intrepid]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide") are not detailed as Hardy. I can use the instructions for Hardy, right?

And about the Restricted Drivers in GUI; there is a driver listed for ATI, it is simply deactivated and doesn't go active whatever I do. It is also attached.

---

### Post by duru on 2009-04-01
By the way, what do I have to uninstall now exactly? And where can I see a list of all installed drivers?

---------------Edit:

I just issued the command **sudo apt-get install linux-restricted-modules-generic restricted-manager** as suggested in ATI Hardy Installation Guide. What I got is
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package restricted-manager is a virtual package provided by:
  jockey-gtk 0.5~beta3-0ubuntu6.1
You should explicitly select one to install.
E: Package restricted-manager has no installation candidate

```

Any lights up?

---

### Post by duru on 2009-04-01
Hi again,

I followed [these]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually") instructions and a lot of things have changed.

First, I didn't exactly know what to uninstall, so I just didn't uninstall anything. I just did what it asks and did everything with no error. (I had errors first time I tried it, but this time I had no errors, I don't know what have changed.)

After fulfilling the steps I issued these commands again to make my two cards work and have a dual head view:
```
sudo aticonfig --initial=dual-head
sudo aticonfig --adapter=all --initial
sudo aticonfig --xinerama=on

```

Now fglrxinfo gives:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
OpenGL version string: 2.1.8543 Release

```

The output of glxinfo is attached.

Now, if I click through GUI menu System>Preferences>Screen Resolution I get nothing. And if I issue **sudo gnome-display-properties**
```
Xlib:  extension "RANDR" missing on display ":0.0".

display-properties-ERROR **: Could not get screen info
aborting...
Aborted

```

If I issue **sudo amdcccle ** I get
```
Parse error on line 23 of section ServerLayout in file /etc/X11/xorg.conf
	"Identifier" is not a valid keyword in this section.
Parse error on line 23 of section ServerLayout in file /etc/X11/xorg.conf
	"Identifier" is not a valid keyword in this section.
Segmentation fault

```

And on my main screen the resolution is not right, and the bottom of the screen is like it is not compiled. I cannot give a screenshot because if I get a screenshot there is nothing wrong.

Thanks for everytihng. Any further help will keep saving lifes.

---

### Post by duru on 2009-04-01
Well, getting there..

[Here]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#AMD_Control_Center"), it says, if you get the error I get, just use lower case letter in xorg.conf. Which I did and ATI Catalyst Control Center could run. There I changed the resolution settings for screens and I got everything right.

So one error left: I still get the one below when I type **sudo gnome-display-properties**:
```
Xlib:  extension "RANDR" missing on display ":0.0".

display-properties-ERROR **: Could not get screen info
aborting...
Aborted
```

And for the third screen; I thought amdcccle could work things out as in Windows but looks like I have to do it by editing xorg.conf. My xorg.conf is attached. The screen on the right is the same with the one on the left.

Any help again and again appreciated.

Edit: Should I uninstall envy now?

---

### Post by markbuntu on 2009-04-01
As far as I know gnome-display-properties does not work with flgrx. It is mostly for the open source drivers anyway. Is your third screen working now? There is some complaints at phoronix forums about 3 screens not working with flgrx.

If envy installed a different driver version than the one you just installed then it is possible that you have more than one set of fglrx DKMS modules and the next kernel update will fail with a DKMS error. But maybe not. Envy often does not load the DKMS modules which is why it fails. You will find out. In the worst case scenario you will need to boot into recovery mode and reinstall the kernel modules so keep them handy since you will be doing that from the command line.

But yes, you can remove envy now.

---

### Post by duru on 2009-04-01
> **markbuntu said:**
> If envy installed a different driver version than the one you just installed then it is possible that you have more than one set of fglrx DKMS modules and the next kernel update will fail with a DKMS error. But maybe not. Envy often does not load the DKMS modules which is why it fails. You will find out. In the worst case scenario you will need to boot into recovery mode and reinstall the kernel modules so keep them handy since you will be doing that from the command line.
This one is really scary.

If gnome-display-properties does not work, then it is ok, ATI CCC does all the trick I need for now.

There is a message coming through the terminal time to time
```
Xlib:  extension "RANDR" missing on display ":0.0".
```
for which the main reason has been enabling Xinerama. My search throughout forums didn't give any useful information about this. I think this will be a cause for some future problems. I installed everything that is like "randr" using Synaptic but it didn't solve the problem.

I think a third monitor may not be a big problem as soon as I succeed to edit xorg.conf. I am wrong, am I not?

Thank you very much for your reply.

---

