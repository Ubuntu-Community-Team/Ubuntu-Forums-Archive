---
title: "Ubuntu doesn't recognise my Soundcard"
date: 2006-12-27
forum: Multimedia &amp; Video
---

### Post by flah11 on 2006-12-27
Hi,

my Creative Soundblaster Live LS! isn't recognized anymore. I installed a new Ubuntu copy today, a few days ago, it just ran fine, the soundcard worked properly. Since I installed the new system, everything connected to sound is just broken...here we go...

cat /proc/asound/cards says:

```
 1 [Bt878          ]: Bt87x - Brooktree Bt878
                      Brooktree Bt878 at 0xddbff000, irq 177 
```

No Soundcard.

But lspci | grep -i audio says:

```
02:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
02:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
```

Oh wonder, a soundcard!!

When I run "sudo modprobe snd-emu10k1 aus", there's no problem reported, but there is still no soundcard when i execute "cat /proc/asound/cards". Just as an info: alsamixer doesn't work too, following message is reported:

```
alsamixer: function snd_ctl_open failed for default: No such device
```

Thanks for your help,

fla.

---

### Post by wesley_of_course on 2006-12-27
Would this help ?


            [http://www.ubuntuforums.org/showthread.php?t=44753&highlight=Creative+Soundblaster](http://www.ubuntuforums.org/showthread.php?t=44753&highlight=Creative+Soundblaster)

                  :-k

---

### Post by majoridiot on 2006-12-27
did you try launching alsamixer with the card switch to explicitly select the sound card?

```
alsamixer -c <card #>
```

also check to see if it's set as default-  System-->Preferences-->Sound

---

### Post by flah11 on 2006-12-27
No, none of that worked, ALSA doesn't even know that there's a soundcard on my system...

---

### Post by majoridiot on 2006-12-27
what is the output from this?

```
 asoundconf list
```

---

### Post by flah11 on 2006-12-27
fabian@becks:~$ asoundconf list
Names of available sound cards:
fabian@becks:~$

---

### Post by esmail on 2006-12-27
FWIW, I am having exactly the same problem .... :-|

---

### Post by tvphil on 2006-12-27
I have Soundblaster Audigy with a similar, but not identical problem as yours. In my case, every time I would boot into Ubuntu Edgy, it would select either the internal Intel soundcard or the PCI variety Soundblaster.First of all, check your sound mixer to see if the "digital/analog" box is checked.If your don't have a sound mixer, download Gnome Alsa Mixer and then look for the box I just described. If it is checked, uncheck it and see if you now have sound.If that doesn't change things for the better, then try the following steps. Several things need to be done, together, they seem to solve the problem. First of all, navigate to the top of the gnome screen to system, then preferences, then scroll down to "sound", click on the middle tab also called "sounds" and select at the bottom where it say's "default sound card" the Soundblaster card, it probably shows the internal sound card by default, this is how you change that. In theory, this should be all you have to do, but wait, there's more!  
Next you have to run a command in terminal  in your normal log in. That command is sudo alsactl store 1, then enter. The number 1 corresponds to your Soundblaster sound card (0 is the internal one you don't want.). Then run the same command without sudo in terminal after logging in as root. If you don't have gnome set-up to log in as root, here's what you do. Again, go to system, then administration and scroll down to user groups. Click on "Root" and click on "Properties". In the password window, create a password, it can even be the same one you use to log in as a user, if that makes it easier. Then go to system, administration and scroll down to login window. Click on the "security" tab and check the box that says "allow local administrator log in". Then you can log in as root whenever you need to and best of all, you stay in Gnome, you don't have to use the terminal to operate under root. Once again, in root, open terminal and type the command alsactl store 1, then enter. Next, still as root, go to system, then preferences and scroll down to "sounds" and select the sounblaster card as the default sound card, then restart. Very important to restart after doing these 2 commands as root. If you hear the bongo drums when your log in box appears after re-starting, then the soundblaster card is working.

---

### Post by flah11 on 2006-12-28
Small update, I found something in dmesg today. How to solve this conflict??!

```
[   40.777804] PCI: Enabling device 0000:02:0a.0 (0100 -> 0101)
[   40.777823] PCI: No IRQ known for interrupt pin C of device 0000:02:0a.0. Probably buggy MP table.
[   40.777856] setup_irq: irq handler mismatch
[   40.777878]  <c0139e82> setup_irq+0x102/0x110  <f8a51fb0> snd_emu10k1_interrupt+0x0/0x480 [snd_emu10k1]
[   40.777920]  <c0139f29> request_irq+0x99/0xb0  <f8a51493> snd_emu10k1_create+0x273/0xbd0 [snd_emu10k1]
[   40.777960]  <f8a501ba> snd_card_emu10k1_probe+0xea/0x370 [snd_emu10k1]  <c01d58b6> pci_device_probe+0x56/0x80
[   40.777999]  <c022aaa4> driver_probe_device+0x44/0xc0  <c022ac1e> __driver_attach+0x7e/0x80
[   40.778022]  <c022a42b> bus_for_each_dev+0x3b/0x60  <c022a9e6> driver_attach+0x16/0x20
[   40.778038]  <c022aba0> __driver_attach+0x0/0x80  <c022a09c> bus_add_driver+0x8c/0x140
[   40.778057]  <c01d5a34> __pci_register_driver+0x34/0x60  <c0130230> sys_init_module+0x140/0x1640
[   40.778116]  <c0102dbb> sysenter_past_esp+0x54/0x79 
[   40.778954] EMU10K1_Audigy: probe of 0000:02:0a.0 failed with error -16
[   40.858542] gameport: EMU10K1 is pci0000:02:0a.1/gameport0, io 0xbc00, speed 505kHz
```

---

