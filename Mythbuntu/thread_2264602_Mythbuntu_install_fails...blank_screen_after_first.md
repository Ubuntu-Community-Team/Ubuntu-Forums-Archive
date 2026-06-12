---
title: "Mythbuntu install fails...blank screen after first boot"
date: 2015-02-08
forum: Mythbuntu
---

### Post by meathead4800 on 2015-02-08
Hi,

I'm nick the new guy on the forum.

I'm trying to run Myth TV on my HTPC(ATX board/case, AMD A6800 APU, no separate video card) 46" TV.  I currently use OpenELEC with no problems.

I installed MythBuntu and the install went fine, got the "install complete please restart your computer".  

Then after I restart it, I get nothing...no splash screen, nothing like it's not even booting.  I can't see it on my network either.

I think this is also related, and strange...I tried Kodibuntu, XBMCBuntu and normal Linux Mint17 Mate all with the same results????  It's not booting.  Then I flashed OpenELEC and it works fine again.

I'e read some things about large monitors not liking stripped down versions of Linux with AMD hardware, could this be the problem?

I have Mint17 Mate on my laptop and Mint17 Cinnamon on my desktop with 42" monitor and AMD CPU and video card, both without problems.

Thanks for any help or ideas.

---

### Post by meathead4800 on 2015-02-09
I'm bumping this thread.

Has anybody recently...within the last few days,  successfully installedMythBuntu on a machine with AMD CPU/GPU and a 42" or larger monitor?

Thanks.

---

### Post by MoebusNet on 2015-02-12
I seem to recall needing to change TTYs after boot by Ctl-Alt-F1 then Ctl-Alt-F7 to get a graphical display due to an old bug. This no longer occurred once the installed system was updated. Mythbuntu 14.04 version 0.27+fixes.

---

### Post by meathead4800 on 2015-02-15
Thanks for your reply Moebus,

I'm not a COMPLETE Linux noob but, what is a TTY and how do I change it.

By the way,  I can"t get the Grub menu to try nomodeset.  I press "shift" during boot and I get nothing.

Like I said, I tried Kodibuntu, XBMCBuntu yaVDR and normal Linux Mint17 Mate/XFCE all with the same results.  This has to be a problem with AMD hardware and Linux.  I read on the KodiBuntu forum the latest kernel broke some AMD systems, but I can't get into a console or Grub menu to try anything...very frustrating.  I don't have any PCs with Intel hardware (way overpriced in my opinion) to try.  

I appreciate all the work that has gone into this and every other Linux distro, but sometimes I think the small or logical things are left out.  For instance, why wouldn"t the "nomodeset" be the default after first boot.  I'm not complaining, just trying to make things MUCH easier for inexperienced Linux users.

---

### Post by Lester_Burnham on 2015-02-15
Are you using a plug in keyboard or wireless? If wireless, does it have an option in the bios to enable usb keyboard support?
Re: TTY. The keys are shown in the post above. ctrl+alt+f1 for tty1, ctrl+Alt+f7 for tty7 (desktop)

---

### Post by MoebusNet on 2015-02-17
@meathead4800: TTY is an abbreviation for a 'terminal emulator' which is a command-line method of entering commands without a Graphical User Interface. The Ubuntu GUI resides on TTY7. To change to TTY1, press-and-hold the CTL, the Alt and the F1 keys simultaneously then release. TTY7 is selected by Ctl-Alt-F7 key combination. Changing from TTY7 to TTY1 then back seemed to make the GUI appear on TTY7 as it should. Once you have the GUI, you can update as normal.

nomodeset is selected by pressing F6 during the boot sequence, scrolling with arrow keys, selecting nomodeset with the Enter key, Escape then resume boot.

---

### Post by roburk on 2015-05-11
Hi
 
I realise this thread is a few months old now, but it is not clear if the OP ever found an answer.
 
I recently reinstalled my mythbuntu mythbackend and ran into the exact same symptoms.
 
In my case my fairly modern gigabyte motherboard had defaulted in the uefi / bios with secure boot enabled. In fact “secure boot” is not an option on my particular MB, I had to set the boot options to “legacy only”, and reinstall.
 
HTH..

Rob

---

### Post by neutron68 on 2015-05-11
My Mythbuntu 12.04 machine has done this exact same thing since I first installed it 2 years ago.  
I keep HOPING this bug will get addressed in an update, but not yet.
Maybe it's not been reported on launchpad??

---

