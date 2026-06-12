---
title: "Mythbuntu 8.10 Hauappage NOVA-T PCI remote"
date: 2009-03-02
forum: Mythbuntu
---

### Post by scottpj on 2009-03-02
Hi, 
I have an oldish Hauppauge NOVA-T PCI DVB card with an IR receiver which plugs in the card. This worked fine on MCE which I hae just ditched in favour on Mythbuntu.

the only buttons I can get to work are:
Left, Right, Up, Down, Select and the numbers 0-9, plus the power button which invokes the shut down dialog.[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

Even when I remove IR support from the Mythbuntu Control Center, I still the same button are active an dth elirc daemon is not running! I don't understand how this working.

I have trawled the wiki's and tried various hardware.conf, lircd.conf and .lircrc files to no avail.

I would have thought if MCE supports this out the box Mythbuntu would too.

Thanks in advance for any help.

---

### Post by scary_jeff on 2009-03-02
I think this means that your remote is being used as a keyboard.

If you run irw in the terminal, and press buttons on the remote, does anything happen?

Run 'cat /proc/bus/input/devices', see if your remote is listed. You should have something like "IR-receiver inside an USB DVB receiver".

Run 'dmesg | grep -s ir', see if anything to do with an infra red remote comes up.

If there's no sign of the remote in any of these, go to post #7 here: [http://ubuntuforums.org/showthread.php?t=994447](http://ubuntuforums.org/showthread.php?t=994447), but you can skip the bit about patching the sourcecode, as those changes are already included in the latest code.

Once you've done what it says in that post, you should see your remote when you run the cat and dmesg commands above. If you can, you need to make sure lirc is installed (sudo apt-get install lirc). Once lirc is installed or proven to be installed. If it wasn't installed already, you will be prompted to select your remote. If it was already installed, run run 'sudo dpkg-reconfigure lirc', and select your remote.

You should then be able to run 'mythbuntu-lirc-generator', which should give you a working remote.

---

### Post by scottpj on 2009-03-02
ok irw - I get returned to the prompt, try again and I get a "connection refused" reply.

Cat /proc/bus/input/devices output:
I: Bus=0001 Vendor=0070 Product=9002 Version=0001
N: Name="cx88 IR (Hauppauge Nova-T DVB-T"
P: Phys=pci-0000:03:09.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1e.0/0000:03:09.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=100003
B: KEY=100fc312 214a802 0 0 0 0 18000 41a8 4801 9e1680 0 0 10000ffc

hardware.conf updated to reflect the "event7"

dmesg output:
[   43.629780] lirc_dev: IR Remote Control driver registered, major 61 
[   43.652079] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[   43.652089] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   43.660129] usbcore: registered new interface driver lirc_mceusb2
peter@mythtv:~$ 

 I have uninstall lirc and run the dpkg-reconfigure lirc successfully, and the mythbuntu-lirc-generator.

Seaching through dsmeg for "input" produced:
   13.677209] input: cx88 IR (Hauppauge Nova-T DVB-T as /devices/pci0000:00/0000:00:1e.0/0000:03:09.0/input/input7

I am tryinthe tip the in the other post about forcing hal to ignore the IR and I substituted the above Hauppauge text for the "IR-receiver inside an USB DVB receiver" version

I am now rebooting to see if this help but it does look a long shot!

---

### Post by scottpj on 2009-03-02
ok the fix to get hal to ignore the IR did not work....lirc did not start and when manually started the IR still did not work at all.

---

### Post by scary_jeff on 2009-03-03
Oh right, you have the version with the USB remote. There's a thread here [http://ubuntuforums.org/showthread.php?t=1068578](http://ubuntuforums.org/showthread.php?t=1068578) where we got a remote like yours working. In the end I think the solution was that he had to select a USB MCE remote when installing lirc, as opposed to a Nova 500 remote.

---

### Post by scottpj on 2009-03-03
Hi, its not a usb IR receiver. I don't know why it seems to be loading a usb driver.... could be my problem. The IR receiver just plugs into the NOVA-T card using a 2.5mm jack plug.

Thanks for the help, but the other posts all seem to have USB receivers and be referring to a NOVA-T 500 card which is not what I have.

---

### Post by scary_jeff on 2009-03-04
> lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC

Did you try the step of "sudo dpkg-reconfigure lirc"? It should allow you to select the nova 500 remote. If you do this, see if the dmesg command gives a different result after restarting.

---

### Post by scottpj on 2009-03-06
Thanks, I have tried that and numerous other options now....in doing so the few buttons that did work now don't. The only way I can get them back is to reinstall. I burned enough time on this.
I will look for a unit that has more widespread use....any suggestions.
 I only want a remote, I don't need the TV card.

---

