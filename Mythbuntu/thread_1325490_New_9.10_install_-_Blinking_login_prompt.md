---
title: "New 9.10 install - Blinking login prompt"
date: 2009-11-13
forum: Mythbuntu
---

### Post by robritz on 2009-11-13
Hello!

The problem: fresh install of 9.10 is having issues. The install process goes smoothly, configuration seems good, then when I restart the machine I get a blinking login prompt (text only, no GUI). Keyboard input corresponds with the blinking, meaning that when the text is displayed, keyboard input works. No text, no keyboard. The blink is quick like a strobe.

Sometimes I am able to hit return a few times, which seems to kick back to the mythbuntu icon and then to a non-blinking text login prompt (no GUI). Entering my username/password does nothing. A message displays occasionally but it's too fast for me to read.

The system: Dell Dimension 4550(?), 2ghz P4, 512mb RAM, 1 400GB drive in sda, 1 320GB drive in sdb. The tuner card is a PCI hauppauge 1600. I'm installing onto the 320GB drive. I've tried both manual partitioning and automatic install. I have not yet tried to install on the 400.

During install I enabled every option (vnc, ssh, etc), and chose NVIDIA drivers for the display. I chose mythtv frontend/backend (default). 

After the installation, the configuration runs perfectly. I have NOT had the computer connected to the network or analog cable signal during configuration, instead planning on doing that afterward (moving to a closet). After restart and removal of the install CD is when I run into the above problems.


I will keep at it, but thought it was worth posting about. Should I try 8.x?

Thanks,

Rob

---

### Post by ZedThou on 2009-11-13
Sounds like the X server is failing to start, so it just keeps trying over and over again. Maybe your video card is a bit older and needs a legacy nvidia driver instead? If you had networking I'd say remote ssh in and stop the gdm service and go from there, but otherwise I guess a rescue disk is in order since mythbuntu doesn't install a grub menu to allow a single user mode boot (someone please correct me if I'm wrong on this point!).

You could also try Alt-Sysreq-k quickly to try to kill everything.

---

### Post by robritz on 2009-11-13
The video card is an nvidia geforce mx 420 (I think), 64mb. VGA and S-Video. I did not try loading the open source drivers, I always selected nvidia, so I will try that next. Thanks!

Edit: I may have also enabled tv-out, which might have thrown the gdm service for a loop? I will try installing with that disabled as well.

---

### Post by ZedThou on 2009-11-13
Your card requires the nvidia 96 series driver, which is why the X server won't start. You'll want to use the open source driver instead and then manually install the 96 series afterwards. It would be nice if the X server didn't keep trying to restart and instead quit after a few failures.

---

### Post by robritz on 2009-11-13
Sweet! I will give that a try. Thanks for the info.

It may be quitting, actually. I thought hitting return at the right time made a difference, but it might just be x server giving up.

---

### Post by sawbuck on 2009-11-13
> **robritz said:**
> Sweet! I will give that a try. Thanks for the info.

It may be quitting, actually. I thought hitting return at the right time made a difference, but it might just be x server giving up.

ribritz,

Don't know if this is relevant but my 9.10 mythbuntu installatiion did the same flashing thing after selecting Nvidia proprietary drivers.  I have a the same capture card as you but an EVGA 6200 (NVIDIA) graphics card which.  In previous installations, I had to edit the menu.lst file and add "vmalloc=256m" at a specific location to use the drivers.  In 9,10 I couldn't find the menu.lst file and stumbled on what looked similar in "grub.cfg".

Here's what I did:

Normal installation ans used proprietary drivers

At the bootloader menu, I selected the safe mode boot

A list of options comes up from which I selected command line boot in safe mode

At the command prompt I enter:

          vi /boot/grub/grub.cfg                   

This opens the grub.cfg file with the simple vi editor (may get warnings of read only file - ignore)

Use the arrow keys to scroll down to the end of the line for the generic kernel.  In myine it is this:

linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e901d7ee-96fa-4c6c-a040-3f4267790bbf ro   quiet splash[COLOR=Red] vmalloc=256m[/COLOR]

Hit the "a" key at the last letter of the line - mine was "h" in splash.  This will move the cursor over one space.

At this point just add the vmallo=(something) with something being a a value usually in 64m increments
At the end of the last key entered hit "esc" key.  This gets you out of the edit mode.

Type  ":w!"  (ignore warnings) this writes the changes to the grub.cfg

Type ":q!" to get back to the original command prompt.

Then reboot.

When I di this it booted OK

Now, I still have to get an answer on how to make it survive a kernel update/upgrade.  I had to redo these steps with the first updater that changed the kernel.

Also, this may not work for you since are cards are different or you may get by using a smaller vmalloc=- value and have success.

Good luck.  I am a noob but did find this to work for me......

---

### Post by robritz on 2009-11-15
sawbuck, installing the open source drivers worked, but thank you for the added info!

---

