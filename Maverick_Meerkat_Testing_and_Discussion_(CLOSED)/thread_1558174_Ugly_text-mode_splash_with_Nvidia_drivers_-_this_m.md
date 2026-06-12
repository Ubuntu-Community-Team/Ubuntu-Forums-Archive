---
title: "Ugly text-mode splash with Nvidia drivers - this may help"
date: 2010-08-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by recluce on 2010-08-21
With the new xorg and nvidia drivers that were installed recently, my plymouth splash screen broke once more to display the text-only "Ubuntu 10.10" message.

Here is one way to fix this, without any changes to GRUB, that worked for me in Lucid and now in Maverick:

1. Install v86d from the universe repository

2. Add the following line to /etc/initramfs-tools/modules:

uvesafb mode_option=<x-res>x<y-res>-<bits>@<refresh> mtrr=3 scroll=ywrap

where 
<x-res> is the x-resolution of the screen mode to use
<y-res> is the y-resolution
<bits> is the colour depth of the mode (8,16,24 or 32 bits)
<refresh> is the refresh rate of the mode (eg. 60 for most TFT screens)

The example in the code box is for 1280*1024 at 60Hz and 32bit colour depth

```

uvesafb mode_option=1280x1024-32@60 mtrr=3 scroll=ywrap

```

3. Run the following command

```

sudo update-initramfs -u

```

Upon the next boot, you should see a nice splash screen in the screen mode you just selected.

Thanks to "whatever" who initially posted the solution above.

---

### Post by cariboo on 2010-08-21
Xserver-xorg-1.9 was released today, so it should show up in the repositories fairly soon. It may be an idea to hold off with the fix, until it's installed.

---

### Post by recluce on 2010-08-25
My test system updated to xorg 1.9 - and the fix still works (no need to re-apply).

---

### Post by VeeDubb on 2010-09-08
First of all, thank you.

There are some truly terrible tutorials floating around regarding how to fix this, and this is one of the only methods that works without BIG drawbacks.

That being said, I followed a slightly larger how-to that included this, and a couple of other steps.  Not sure if that was necessary or not.

None, the less, let me add the additional things I did.

1. After installing v86d I ran the following command to get a list of framebuffer modes that work on my system.  This was an important step because although my desktop monitor's native resolution was a supported frame-buffer size, the native resolution of my netbook was NOT

```
sudo hwinfo --framebuffer
```

2. I also, following the other tutorial, modified my /etc/default/grub.  (don't forget sudo update-grub2 after you make your changes)  I'm not sure if this was actually necessary, but it did no harm.

```
........
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24@60,mtrr=3,scroll=ywrap"
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
........
```

Note that instead of replacing or modifying the original GRUB_CMDLINE_LINUX_DEFAULT entry, I simply commented it out.  This is a VERY good practice, as it allows you to revert the changes if you make a mistake.  I would recommend doing the same thing to the modules file.  Mine looks like....

```
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
#The next line was added by steve to fix plymouth
uvesafb mode_option=1680x1050-24@60 mtrr=3 scroll=ywrap
```

Again, this is a good practice for many reasons, but especially if things change and this fix is no longer needed.

Plymouth now looks beautiful on my desktop, and passable on my netbook.  I still have my VTs, and they are at the proper resolution for my monitor.

The only real mystery is why Ubuntu does not do this for us.  I understand why the default install has the open source drivers, but I see no technical reason why the postint scripts for the ubuntu nvidia packages wouldn't be able to check your monitor's resolution and set this up for you.

---

### Post by VinDSL on 2010-09-08
Nice one!  =D>

Worked a treat for 10.10.  Now it looks like 10.04.1 :D

Um...  And, I'm serious.  Thanks!

---

### Post by VinDSL on 2010-09-08
> **VeeDubb said:**
> 1. After installing v86b[...]I couldn't find v86b, so I used v86d.

I melded your tutorial with the OP's, and it worked on the first go-round!

---

### Post by VeeDubb on 2010-09-08
> **VinDSL said:**
> I couldn't find v86b, so I used v86d.

I melded your tutorial with the OP's, and it worked on the first go-round!

You are correct.  The OP made a typo and then I made the exact same typo.  It is, and should be, v86**d**.

I've corrected my post.  Glad it worked for you anyway.

On a related note, even if your monitor's native resolution doesn't appear as a supported resolution, you should try the native resolution and refresh rate anyway.  It probably won't work, but it might, and will look better if it does.  Just be prepared to fail, and if worst comes to worst, be ready to do a failsafe boot and fix it from a command line.

---

### Post by VinDSL on 2010-09-08
> **VeeDubb said:**
> On a related note, even if your monitor's native resolution doesn't appear as a supported resolution, you should try the native resolution and refresh rate anyway.[...]I'm running a Dell 1907FP monitor (no wide-screens for me) so my res is exactly the same as the OP's example code.

Heh!  That made it simple...

With your addendum, it worked the first time.

On average, I (probably) have a 90% failure rate, playing around with Linux splash screens, but...

I beat the odds this time!  :lolflag:

---

### Post by amac777 on 2010-09-08
I tried with just Recluse's solution and still had the weird resolution for plymouth. I then modified the grub2 config as VeeDubb pointed out and that did the trick. Got a nice boot up screen now.

Also, as VeeDub noted, my monitor's native resolution was not on the list but I tried it anyway it worked.

Thanks to both of you!

---

### Post by caryb on 2010-09-09
I tried this on my stinkpad (1366x768) & I got a trip down memory lane, CGA graphics (think 100 font size) I also tried 1024x768 with no real difference.

Bugger Cary

---

### Post by VinDSL on 2010-09-09
> **caryb said:**
> [...]I got a trip down memory lane, CGA graphics (think 100 font size) I also tried 1024x768 with no real difference.[...]Did you run:

```
sudo hwinfo --framebuffer
```

I just discovered there's no 32-bit mode at native res, on this machine -- even though it seemed to be working.  ;)

```
$ sudo hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Hardware Class: framebuffer
  Model: "NVIDIA G73 Board - p456h0  "
  Vendor: "NVIDIA Corporation"
  Device: "G73 Board - p456h0  "
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 256 MB
  Memory Range: 0xe0000000-0xefffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

EDIT

I ran the commands again, and restarted.  

The splash screen looks better now (@ 24 bits)...  =D>

---

### Post by MarkieB on 2010-09-09
no longer participating in ubuntuforums.org

---

### Post by VeeDubb on 2010-09-09
> **MarkieB said:**
> ...is it really worth bothering?

To me?  Yes.

The fix that I used, takes a total of 3-5 minutes total.  Granted, it took the better part of half an hour to find the best fix, but once I found it, I only had to spend a few minutes doing the actual fixing.

Install one package from the repos, run one command to make sure you pick sane options, edit two text files, run two more commands.  Done.

I have probably spent far more time discussing this here than it took me to actually get it fixed.

---

### Post by VeeDubb on 2010-09-09
> **caryb said:**
> I tried this on my stinkpad (1366x768) & I got a trip down memory lane, CGA graphics (think 100 font size) I also tried 1024x768 with no real difference.

Bugger Cary

Can you please post the contents of your /etc/default/grub and /etc/initramfs-tools/modules

I suspect you have something configured incorrectly there, and if you post them I'd be happy to take a look.

---

### Post by chrismine on 2010-09-09
One can also fix this by installing StartUP-Manager from Software Center and choose your options in the program.

---

### Post by Helkaluin on 2010-09-09
Instead of fiddling with alternative framebuffer drivers, a simple line of GRUB_GFXPAYLOAD_LINUX=<whatever resolution> in /etc/default/grub did the trick for me in a much simpler way.

---

### Post by caryb on 2010-09-09
I didn't install hwinfo as I'm running Kubuntu & thought it was a Gnome app that would install Gb's of data! WRONG have installed it now...

root@stinkpad:~# hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.NszzKie+Nl9
  Hardware Class: framebuffer
  Model: "NVIDIA Quadro NVS170M
"
  Vendor: "NVIDIA Corporation"
  Device: "NVIDIA Quadro NVS170M
"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xcf000000-0xcfdfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0363: 848x480 (+3392), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown



root@stinkpad:~# cat /etc/default/grub 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

root@stinkpad:~# cat /etc/initramfs-tools/modules
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
uvesafb mode_option=1366x768-32@60 mtrr=3 scroll=ywrap

Just tried uvesafb mode_option=1600x1200-24@60 mtrr=3 scroll=ywrap

Still GGA, it also starts X in low graphics mode with this enabled & I have to restart X to get back to 1366x768 mode.

Cary

---

### Post by seeker5528 on 2010-09-09
> **VinDSL said:**
> I just discovered there's no 32-bit mode at native res, on this machine -- even though it seemed to be working.  ;)


When hardware came along that claimed it had 32 bit color, some of the earlier Linux drivers provided a 32 bit option, but some literal minded person or group decided that 'Hey!! 32 bit still only has 24 bits of color, so you should only have to specify 24 bit and the +8 should be handled automatically when the hardware supports it.' so that's what was adopted for all the drivers. 

I'm sure there is a longer story out there somewhere, but do you really want to know? :p

Later, Seeker

---

### Post by VeeDubb on 2010-09-09
caryb, you shoudl have read the whole post and not just the OP.  The OP's directions seem to be incomplete.

You need to modify your /etc/default/grub

Find the line that says

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and replace it with 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1366x768-32@60,mtrr=3,scroll=ywrap"
```

Then run ```
sudo update-grub2
```

Please not that this will probably not work.  You may well have to change the "-32" in your grub file AND modules file to "-24" and update both again.  As you can see from the results of hwinfo, your system does not appear to support 32bit framebuffers.

---

### Post by VinDSL on 2010-09-10
> **VeeDubb said:**
> To me?  Yes.

I think it's worth it too!  I know it's only aesthetics, but...

> **VeeDubb said:**
> Install one package from the repos...Sorry for being a stickler, but I had to install two packages:

[LIST=1]
[*]v86d
[*]hwinfo
[/LIST]
):P

---

### Post by VeeDubb on 2010-09-10
> **VinDSL said:**
> Sorry for being a stickler, but I had to install two packages:

[LIST=1]
[*]v86d
[*]hwinfo
[/LIST]
):P

Not sure what it's a dependency of, but hwinfo must have been a dependency for something else I'd already installed.  It was already on my system.  Good to know that it isn't part of the default install.

---

### Post by cariboo on 2010-09-10
If you're not sure about dependencies, you can always open synaptic, highlight the package then click Properties->Dependencies.

---

### Post by VeeDubb on 2010-09-10
> **cariboo907 said:**
> If you're not sure about dependencies, you can always open synaptic, highlight the package then click Properties->Dependencies.

It's the other way around.  I know what it's dependencies are, but don't know what it's a dependency OF.  It was automatically installed for me as a dependency of something else, and I'm not sure what.

---

### Post by seeker5528 on 2010-09-10
> **VeeDubb said:**
> It's the other way around.  I know what it's dependencies are, but don't know what it's a dependency OF.

Same thing except on the dependencies tab you change it to show 'dependent packages'.

Of if you want you could install apt-rdepends, open a terminal window and type:

```
apt-rdepends update
apt-rdepends -r -f Depends,PreDepends,Recommends some-package
```

or if you are logged in at the command line you probably want to do:

```
apt-rdepends -r -f Depends,PreDepends,Recommends some-package | less
```

Later, Seeker

---

### Post by ktp on 2010-09-10
apt-rdepends is nice.

---

### Post by seeker5528 on 2010-09-10
> **ktp said:**
> apt-rdepends is nice.

Except I haven't quite figured out the logic that you have to specify '-r' to get the reverse depends. Isn't reverse what the R stands for in apt-rdepends? :roll:

Later, Seeker

---

### Post by ktp on 2010-09-10
hehe first thing that I thought when i first saw it.

---

### Post by monty47 on 2010-09-19
thanks a lot recluce it's working like a charm

---

### Post by dentarthurdent on 2010-10-04
worked here for me too! thanks!

---

### Post by recluce on 2010-10-05
> **VeeDubb said:**
> caryb, you shoudl have read the whole post and not just the OP.  The OP's directions seem to be incomplete.

You need to modify your /etc/default/grub

Find the line that says

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and replace it with 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1366x768-32@60,mtrr=3,scroll=ywrap"
```

Then run ```
sudo update-grub2
```

Please not that this will probably not work.  You may well have to change the "-32" in your grub file AND modules file to "-24" and update both again.  As you can see from the results of hwinfo, your system does not appear to support 32bit framebuffers.

Apparently, for some people changes to GRUB seem to be required to make it work. Certainly not for me, I am not even running GRUB2 - and my GRUB1 starts into the graphical splash screen just fine with just the options "quiet splash".

I don't see the need to repeat the VESA graphics settings in GRUB, but I would suspect that "nomodeset" might be required for some chipsets.

So my original "how to" should work for most people, if it doesn't, it is time to try VeeDub's additional modifications.

---

### Post by mc4man on 2010-10-05
For those interested here is the orig. 'workaround' post and reasons for doing this way 
[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

---

### Post by MarkieB on 2010-10-08
no longer participating in ubuntuforums.org

---

### Post by rogeriovinhal on 2010-10-10
This fixes didnt work at all for me at 10.04. I now upgraded (with dist-upgrade) to 10.10 hoping it would be fixed, but no good. Still tried some more things, but it wont work at all.

I have a Geforce GTX260 with a 1920x1080 native 22" LCD monitor. As this res is not supported, I chose 1680x1050. Grub apeears in high resolution, but right after it loads the kernel it changes back to 640.480 and only stretches the logo to fit in the whole screen, but still in low res.

My hwinfo --framebuffer:

```

02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.VsfXBTyKB3F
  Hardware Class: framebuffer
  Model: "NVIDIA GT200 Board - 08970053"
  Vendor: "NVIDIA Corporation"
  Device: "GT200 Board - 08970053"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xf9000000-0xf9dfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037b: 1280x720 (+5120), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

My /etc/default/grub:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24@60,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1680x1050

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

my /etc/initramfs-tools/modules:

```

# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
uvesafb mode_option=1680x1050-24@60 mtrr=3 scroll=ywrap

```

This is the exactly same thing I had when I tried to fix this when 10.04 was out. I just kept on struggling to make it work and eventually gave up. I am about to do the same right now. :(

---

