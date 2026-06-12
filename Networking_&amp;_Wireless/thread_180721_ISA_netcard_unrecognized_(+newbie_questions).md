---
title: "ISA netcard unrecognized (+newbie questions)"
date: 2006-05-22
forum: Networking &amp; Wireless
---

### Post by Csabo on 2006-05-22
Hi everyone,

I've been really interested in Linux for a long time, and a few weeks ago I installed Ubuntu linux 5.10 on my old computer from a CD which I downloaded. Off topic: I'd like to thank everyone who made these wonderful pieces of software possible. As I'm new to linux itself, I'm still just learning and discovering things, and it's tons of fun. I can't believe that  I got an OS and all this quality software for free. I can't even begin to image how much work must have gone into all of this.

I've been surprised how well it recognized all my hardware so far, even my USB key and DVD writer, with one exception: an ISA network card. That's why I'm posting now (from another computer), as I can't connect to the internet yet.

The card is "AcerLan". When I plug the cable into the network card, I can see a green light coming on, so I think the card itself works.

I've searched the forums and tried a lot of the suggestions. In the troubleshooting guide for wired connections, I'm already stuck on the first thing. When I run "sudo mii-tool eth0", it replies "SIOCGMIIPHY on 'eth0' failed: No such device". So, here are my list of newbie questions:

1) It doesn't look like there's an "Add new hardware" equivalent in Ubuntu. Is it true that everything should be just detected automatically? Or is there some option to tell the OS that there's a piece of hardware in the machine?

2) I learned about the 'lspci' command, which produces this output:
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:04.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:04.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:04.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:04.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:00:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:00:0c.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage IIC AGP (rev 7a)

There's no 'lsisa' command to list ISA cards, is there? Are ISA cards supposed to be showing up in the same list along with PCI cards?

3) In this thread: [http://ubuntuforums.org/showthread.php?t=168915&highlight=isa+network+card]("http://ubuntuforums.org/showthread.php?t=168915&highlight=isa+network+card")
another gentlem was talking about a similar problem. He used the modprobe command, but as a parameter he used "eepro", which is the 'system name' of his ISA card. I wonder where one would find that name from? I guess if Ubuntu recognized my card, it would be in the 'lspci' list?

Thanks in advance for any help,

Csabo

---

### Post by az on 2006-05-22
You probably need to go into your bios and tell it to not expect that you are running a pnp aware OS.  You may also be able to find out what ressources it needs (irq and so forth) and you may be able to tell your motherboard to dedicate this irq to the ISA bus.

The driver for your card may possibly be calle ne

sudo modprobe ne

if that works, add the word "ne" at the end of the list in /etc/modules so that it gets loaded every time you boot.

---

### Post by Csabo on 2006-05-22
Thanks for the suggestions azz. I checked my BIOS, it does have a "PNP OS Install" option, but it was already on No. I could not see any places that would list what IRQs or DMAs (if any) the card uses, nothing in the BIOS, and nothing on screen during startup.

I tried "sudo modprobe ne", but it doesn't display anything at all (not even an error message), just returns to the prompt. Is that normal?

I have a new piece of information. I finally found the entry for my ISA card in the Device Manager! (That's another score for Ubuntu, I thought it didn't see the card, but it does.) It's listed as **PnP Device (ANX3101)**, on the right side it's all "unknown". Googling ANX3101 gives me the windows drivers and the full name of the card: "AcerLAN ALN-101 PnP Ethernet Adapter". So my question is now quite specific:

4) How do I get Ubuntu to work with an AcerLAN ALN-101 PnP Ethernet Adapter card?

Again thanks for any help in advance.

Csabo

---

### Post by Slim Odds on 2006-05-22
[QUOTE=Csabo]Thanks for the suggestions azz. I checked my BIOS, it does have a "PNP OS Install" option, but it was already on No. I could not see any places that would list what IRQs or DMAs (if any) the card uses, nothing in the BIOS, and nothing on screen during startup.[/QUOTE]

azz's point was, you DON'T want it ON. You want it OFF.

---

### Post by az on 2006-05-22
[QUOTE=Csabo]
I tried "sudo modprobe ne", but it doesn't display anything at all (not even an error message), just returns to the prompt. Is that normal?[/QUOTE]

Yes.  If it loads fine without errors, you should then see an eth0 device to configure....  Load the module and then go to the network configuration thinggie.

---

### Post by Csabo on 2006-05-24
Woo-hoo! I'm posting this from Ubuntu using Firefox :D

First of all sorry for the late reply but I didn't have time to try the suggestions yesterday.

Slim Odds, thanks for the comment, but I think you misread what I wrote. The BIOS setting was on "No", as in "No, my OS is not PNP aware". The other setting was Yes.

azz, I tried the modprobe command again, then went to System|Administration|Networking, and there it was: the eth0 interface. However, I got stuck on another stupid newbie issue: I can't edit /etc/modules. I opened the file in the text editor but it was read-only. Should I be using a special command from the terminal instead?

So I tried something else: I grabbed a PCI network card from work (we had a box full of them), popped it in, and voila, Ubuntu detected it, and eth0 was there by itself. Very impressive! I then followed the wired ethernet tutorial again, after a bit of a struggle, I came up with two issues, but solved both.

1) I did have to remove ipv6, like the tutorial suggested. Renamed it, restarted, and now my IP is ok.

2) I could ping IP addresses but nothing by name. As the tutorial said I had a DNS problem. I tried "cat /etc/resolv.conf" as they suggested but there was nothing, just the prompt again. On my Win machine, it seemed to find the DNS servers on its own. Eventually I typed a correct DNS server number into Network settings|DNS, and here I am!

So, again a few more questions (adding to the ones above):

5) How do I edit /etc/modules so that it's not read-only?

6) How can you get the DNS dynamically?

7) Now that 4) is answered (basically for this card the "ne" driver is needed), what does one do to "help" the project? That is, is there a place where I can go and add this information? I assume Ubuntu has some kind of lookup table somewhere. If we added this piece of info (ANX3101 -> ne), maybe the next person using Ubuntu with this same type of card won't have any trouble.

8) Where can I make a suggestion to change the modprobe command so that it outputs something? I think a simple "modprobe ok" type response would be great feedback, especially for beginners. Or is it just understood that unless you see an error message, everything went well?

If anyone knows the answers to my inital questions (re: ISA cards, etc), I'd be still very interested to know, just out of curiosity. Thanks for all the help guys! Ubuntu rules!

---

### Post by Iowan on 2006-05-25
[QUOTE=Csabo]5) How do I edit /etc/modules so that it's not read-only?[/QUOTE] Didja **sudo nano /etc/modules**?
(or would it be gksudo for nano?)

---

### Post by az on 2006-05-25
The issue with isa hardware is known.  It is unsafe for the kernel to load the modules by itself.  That could result in the box locking up every time you booted.  So it just ignores most isa hardware.

Since that hardware is mostly extinct, there is not a lot of effort to get some sort of framework going which can load the drivers automagically, but safely.  Perhaps there can be something done with HAL and udev, but I dunno.

Maybe just file a bug report or add to an existing one.

As for DNS, I'm not quite sure what you mean.

---

### Post by Csabo on 2006-05-26
Iowan, that worked, thank you!

azz, thanks for the information on the ISA cards. You are right, they are not that common anymore, and PCI network cards are inexpensive anyway. I guess we're all better off if the dev teams spend their time developing support for more modern hardware.

For the DNS, I figured it out. I got the eth0 working by specifying a static IP, and that's probably why I manually had to input a DNS server IP too. I switched it to DHCP (my router has DHCP enabled), and it got an IP and seems to know the DNS server on its own too.

Next I will try to get wireless access, but I'm still reading up on that. If I can't solve it, I'll open a new topic. Thanks for the help guys!

---

### Post by helpdeskdan on 2006-06-05
Thanks all; this was also the answer to my problem.

---

