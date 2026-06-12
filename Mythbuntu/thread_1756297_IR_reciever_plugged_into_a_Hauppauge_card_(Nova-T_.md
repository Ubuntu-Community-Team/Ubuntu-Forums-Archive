---
title: "IR reciever plugged into a Hauppauge card (Nova-T DVB-T)"
date: 2011-05-12
forum: Mythbuntu
---

### Post by Daminator on 2011-05-12
Hello all,

I've been using MythTV for years and moved over to MythBuntu shortly after it was started. It's a great thing and makes life much easier!

I really need some help getting my remote control set up. I have had this working before, a couple of years ago, but the instructions I followed back then do not work any more.

Once my remote it working, I have a file that has all of my preferred key configurations etc, I just need the hardware working.

Is there any option I can choose from the MythBuntu Control Centre that would set up lirc to use the IR receiver that plugs directly into the back of one of my Hauppauge Nova-T cards?

If not, can anyone help me do that?

I've tried so many thing that I'm not sure lirc even loads properly any more and I can't bare to spend more time in config files that I don't understand. Life's too short.

failing that, is there a way to buy myself out of trouble? Would buying a USB IR receiver 'just work', or dome other purchase? I'd rather spend a few £/$ than loose more hours of my life in frustration.

Looking forward to any comments.

---

### Post by nickrout on 2011-05-12
Does hauppauge Nova-T 500 not work for you?

---

### Post by Daminator on 2011-05-12
No it doesn't. That's what it's set to at the moment.

Isn't that selection just for the key mappings? It's the hardware talking to lirc I think I'm having trouble with.

---

### Post by rtrevor on 2011-05-12
This works for me (might want to grab a backup copy of /etc/lirc/hardware.conf and ~/.lirc/mythtv first as they will be overwritten):


Run "sudo dpkg-reconfigure lirc"

Remote type: Linux input layer (/dev/input/eventX)
IR transmitter: none
Device: select the IR device (has "event-ir" in the name iirc)


Once that's done, run "mythbuntu-lircrc-generator" which will generate key mappings for you.

However at the moment there's a bug causing it to create two button presses for every key so:

Run "gedit ~/.lirc/mythtv" and remove the second set of duplicate entries (find where KEY_0 appears again and delete it and everything after it)

All being well, should now be working with all keys correctly mapped

---

### Post by Daminator on 2011-05-12
Certainly sounds good! I'll try this when I get home with my fingers crossed!!

Do I need to do anything different to take into account the face that I have 2 Nova-T cards in the machine?

I know one is on Event6 and one is Event7, but don't know which the IR cable is plugged into.

Thanks for the quick replies!

---

### Post by Daminator on 2011-05-12
Ok, not I'm really confused.

rtrevor's advice seemed spot on, and I'm sure it would have worked from my previous state, but nothing is happening now.

Previously, even when the remote wasn't working, numbers were at least being recognised (in a terminal or wherever) so that I knew the hardware was functioning.

Recently (last few days, since last tried fixing this myself), even number inputs aren't coming through.

I was hopeful that rtrevor's advice would fix all wrongs and get me back on track, but no. Nothing is being received at all.

I have just tried changing the batteries, but they were quite new anyway.

I've tried both
/dev/input/by-path/pci-000:01:08.2event-ir and
/dev/input/by-path/pci-000:01:06.2event-ir
both with the same effect.

I've tried running 'irw' after both attempts with 'sudo dpkg-reconfigure lirc', but still nothing is coming through at all.

Any tips?
I've checked that the lead is still plugged in.

---

### Post by Daminator on 2011-05-12
I have tried:

- a second Hauppauge remote control that I have (since I bought 2 cards)
- plugging the IR receiver into the other card
- changing batteries

and I can't get the system recognising 'anything' from the remote.

As I said, numbers have always worked on the remote, so I don't know what's going on.

I would think that it was a hardware problem (the IR lead??) except for the fact that I feel like I know the instant that it stopped working. I'm sure it was during one of my 'attempting to fix by editing config files' sessions. One minute it was working (not 'working', but numbers at least being recognised), the next it stopped.

Any ideas what I can do next?

---

### Post by Daminator on 2011-05-15
Bump,

Is there anything I can do to test my hardware, or do I just need to give up and try buying something else?

Any advice on an IR receiver that will just plug into MythBuntu and work without any messing around?

---

### Post by Cuppa-Chino on 2011-05-15
> **Daminator said:**
> Bump,

Is there anything I can do to test my hardware, or do I just need to give up and try buying something else?

Any advice on an IR receiver that will just plug into MythBuntu and work without any messing around?

yip I am looking for one too -- I am actually moderately excited about this thingy mabobs but not sure if it will work out of box:

[http://www.pulse-eight.com/store/products/96-motorola-nyxboard-hybrid.aspx]("http://www.pulse-eight.com/store/products/96-motorola-nyxboard-hybrid.aspx")

---

### Post by johalareewi on 2011-05-15
I have a T-500 dual tuner DVB-T card with the remote and it works with Mythbuntu 10.10.  Here's how I did it.

1) Install Mythbuntu and select Nova T-500 as the remote. 

2) Configure for using lirc as follows:- 

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500) 

Scroll down to the using lirc section, in particular... 

Mythubuntu case 

On mythubuntu 10.10, you just have to add this line in /etc/udev/rules.d/65-persistent-hauppauge.rules  (this file had to be created) 

SUBSYSTEM==&quot;input&quot;, KERNEL==&quot;event*&quot;, ATTRS{idVendor}==&quot;2040&quot;, ATTRS{idProduct}==&quot;8400&quot;, SYMLINK+=&quot;lirc0&quot; 

Then I created an empty .irexec file in ~/.lirc 

This was enough to get the basic remote working.

---

### Post by nickrout on 2011-05-15
your quoting is all screwed up:

```
SUBSYSTEM=="input", KERNEL=="event*", ATTRS{idVendor}=="2040", ATTRS{idProduct}=="8400", SYMLINK+="lirc0"

```

---

### Post by nickrout on 2011-05-15
> **Cuppa-Chino said:**
> yip I am looking for one too -- I am actually moderately excited about this thingy mabobs but not sure if it will work out of box:

[http://www.pulse-eight.com/store/products/96-motorola-nyxboard-hybrid.aspx]("http://www.pulse-eight.com/store/products/96-motorola-nyxboard-hybrid.aspx")

it should work, but it is not available yet, pre-order only. It's not a huge wad of cash to be a tester :)

There is a thread about it on the mailing list, you'll fine it in the archives.

---

