---
title: "Nice-- How do I use it to change my change-channel script priority?"
date: 2007-11-19
forum: Mythbuntu
---

### Post by linuxlibrarian on 2007-11-19
This is probably an insanely dumb question... But I can't seem to figure out if there's even a way to do this.

Sometimes, my channel change script misses numbers. For instance, I want to go to channel 244 and it goes to 24 or 44.  

I have tried changing the "Sleep" time in my script. That helped a little, but it still, on occasion, I miss a number (usually the first one or the second one).

I have searched around, and I discovered that some people have solved the problem using the command nice --15 to change the priority of the channel change script. I don't know as this would solve my problem, but I'd like to try it.

Here's the issue: to run nice at a helpful priority level (most places I've been say -15 is appropriate) I need to be root. I don't want to run my myth frontend sudo, or even run the channel change script sudo.

I'm not sure that even giving my user permission through a  sudoers file would help... I am confused by what I am reading... And if it would, I'm not entirely sure how to do it...

My questions are these: 

1) Is it possible to set a different priority for the channel change script through the Mythbuntu set up menus?

2) If not, is it possible to change the priority of the script without running the Myth user as root? With Sudoers? How would one do that? Changing a setting/launching a process at start up? How would one do that? (I know nice can only be run by someone with root privileges.)

Thanks in advance. Sorry if I'm a little slow. I've been using Linux several years, and never once had to use nice. Odd.

shoe

---

### Post by foxbuntu on 2007-11-19
To answer your questions:

1) No. At this time the Mythbuntu Setup Menus do not have any advanced systems administration tasks such as nice

2) As far as I know you would have to run nice as sudo in-order change running priority.

However on that same note this sounds like a latency issue with your change method. What are you using? IR Blaster? Serial cable to STB?

---

### Post by mdkendall on 2007-11-20
If the situation is that you are changing channels using a remote which is being received by a receiver attached to your your Myth box, which is then using a transmitter ("blaster") to send a channel change command to a set-top box, then the problem may be concurrent transmissions.

I saw this for example when pressing 4-2-Enter on a remote. As soon as I pressed Enter, Myth invoked the channel change script which started to send the first '4' to the set-top box. However, because it happens so fast I still had my finger on Enter and the set-top box saw both the transmissions at the same time, resulting in confusion. If I just pressed 4-2 and waited for the timeout to initiate the transmission it worked.

The solution was to include an initial delay (sleep 1) in the channel change script to give time for one transmission to finish before the other started. (In fact, the script did initially have such a delay before I hacked about with it trying to make it faster. I now understand what it was for.) An alternative approach would be to ensure that the set-top box can only see the transmitter attached to the Myth box, and is shielded from any remotes the user is waving around.

---

### Post by linuxlibrarian on 2007-11-20
Thanks guys.

I am using the Hauppauge PVR-150 MCE remote with the usb ir blaster that comes with it. (It came with the really yucky black Vista remote).

I have been playing with the sleep function in the script. I notice it is a bit more responsive when I actually make the sleep time shorter (it was at 1, I changed it to 0.4, which I have seen in other scripts, and it did seem to work a little better.)

That was, until my husband tried to change channels. His channel changing cadence is a little different than mine.

Here's the thing though... It's not missing channels just when I use the remote. It's missing them when I schedule recordings, too... sometimes. Which *would* lead me to believe it possibly could be a latency issue, like foxbuntu said... 

I have fiddled with pci latencies on the PVR-150, but either I don't know what I'm doing and don't set it high enough, or too high... but things seem to have no real improvement when I do that...

Here's my set up, FWIW:

I have an AMD Athlon 64 2.4 Ghz chip (single core)
1 gig RAM
250 gig SATA hdd
PCI wireless card
Hauppauge PVR-150 MCE
Biostar TForce 7050 M2 motherboard
On board Nvidia graphics/sound (using TV Out)

My DirecTV box is a Philips DSX5250.

It seems to be only certain channels, now that I'm thinking, that miss digits... Mostly in the 200's. 296 is one that consistently doesn't record when I schedule it to. It records 96, or some other iteration of those numbers. 244 can be a little odd too. The rest of the 200's seem to not "miss" quite as much. The OSD shows the correct channel, but the receiver misses the the first digit.

I'd be willing to try tweaking latencies again... I've used the instructions on the mythtv wiki to do it, but are there any hints you might have? For instance, "Don't chose a latency less than x or more than y"

And what's the best way to get it to stick across reboots in Mythbuntu, once I find one that works well? Will a script in the "Autostarted applications" of Xfce work?  I have tried seeing if my motherboard will allow me to change the latency, but the BIOS is less than user friendly.

Thanks again!

---

### Post by linuxlibrarian on 2007-11-24
In case anyone else is having the same problem, I thought I'd post my solution.

I put an extra sleep argument in the change channel script, before the first digit was called...

It goes before the "system" line in channel-change-lirc.pl 

I set it to sleep 0.2;

This pauses the system enough that the channel number can transmit fully to the STB, and I seem to be having pretty good luck with it thus far.

shoe

---

