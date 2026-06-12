---
title: "Ethernet not connecting at 1000mbps"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by mmad on 2011-04-27
I've been doing some reading and I cannot work out why I'm having this problem. My 32-bit Ubuntu Server running 10.10 has a Realtek RTL8111 ethernet card which supports up to 1000mbps. However, when I run **sudo ethtool eth0** I get:


```
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes
```


After running **sudo ethtool -s 1000** to try and change speed to 1000mbps, the output is still the same as before. Why is this :S?

---

### Post by Buntumatic on 2011-04-27
Because your switch is 100 Mbit/s ?

---

### Post by mmad on 2011-04-27
> **Buntumatic said:**
> Because your switch is 100 Mbit/s ?

Nope. The switch is a gigabit switch and my laptop connects to it at 1Gbps. I should also add at this point that I am using a cat5e cable, so that shouldn't be the problem either.

---

### Post by Buntumatic on 2011-04-27
RTL8111 ... Google tells there may be some driver confusion with this card. Are you sure correct driver is loaded?

---

### Post by mmad on 2011-04-27
> **Buntumatic said:**
> RTL8111 ... Google tells there may be some driver confusion with this card. Are you sure correct driver is loaded?

I downloaded the latest driver, and installed it. Still the problem persists :/.

---

### Post by Buntumatic on 2011-04-27
Installing and using are two different things. Let me repeat the question, are you sure correct driver is loaded?

---

### Post by mmad on 2011-04-27
> **Buntumatic said:**
> Installing and using are two different things. Let me repeat the question, are you sure correct driver is loaded?

I followed the instructions in the README file supplied with the driver. I did do some research and as far as I understood the faulty driver hides the 1gb option completely - something which my system does not.

---

### Post by Buntumatic on 2011-04-27
Based on information you have provided I'd say there are two possibilities left:

Your card does not support 1000 Mbit/s

The driver that is loaded does not allow it. What's loaded can be seen with [COLOR=Blue]lsmod[/COLOR], if wrong driver is loaded you may need to blacklist it.

---

### Post by mmad on 2011-04-27
```
Module                  Size  Used by
joydev                  8767  0
**r8168 **                161898  0
hidp                   11664  0
hid                    67742  1 hidp
rfcomm                 33811  4
binfmt_misc             6599  1
sco                     7998  2
bnep                    9542  2
l2cap                  37008  17 hidp,rfcomm,bnep
vboxnetadp              6454  0
vboxnetflt             15152  0
vboxdrv               190647  2 vboxnetadp,vboxnetflt
parport_pc             26378  0
ppdev                   5556  0
snd_hda_codec_atihdmi     2411  1
snd_hda_codec_realtek   218492  1
snd_hda_intel          22299  2
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_                                                                                                                               hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
fglrx                2252898  32
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  11001  2
bluetooth              50500  10 hidp,rfcomm,sco,bnep,l2cap,btusb
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_cod                                                                                                                               ec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0
agpgart                32075  1 fglrx
soundcore                880  1 snd
lp                      7342  0
serio_raw               4022  0
i2c_piix4               8795  0
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
k10temp                 2607  0
parport                31492  3 parport_pc,ppdev,lp
shpchp                 29982  0
ahci                   19198  3
mii                     4425  0
libahci                21792  1 ahci
pata_atiixp             3288  0
```

I believe that's the driver that I'm supposed to have.

Also: [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D%28L%29%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8168E](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D%28L%29%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8168E) suggests that this does support gigabit ethernet.

There seems to be conflicting evidence. Officially 1000mbps is supported, but on my network it isn't working :(.

---

### Post by Buntumatic on 2011-04-27
What card is it exactly.

```
lspci -nn | grep -i eth
```

---

### Post by bowens44 on 2011-04-27
You say you are using a cat5e cable. Is it the SAME cable that you used to connect your laptop? The reason that I ask is that I had a similar issue and it turned out to a cat5e cable that would do 100mps all day long but would not do 1000mps at all.

---

### Post by mmad on 2011-04-27
> **Buntumatic said:**
> What card is it exactly.

```
lspci -nn | grep -i eth
```

The command returns:

```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
```

---

### Post by mmad on 2011-04-27
> **bowens44 said:**
> You say you are using a cat5e cable. Is it the SAME cable that you used to connect your laptop? The reason that I ask is that I had a similar issue and it turned out to a cat5e cable that would do 100mps all day long but would not do 1000mps at all.

It is not the same cable, but I bought them from the same person and they seem to be identical, well other than the fact that the server's cable is twice the length (its 15m whilst the laptops is only 8m). I know that cable length could be a deciding factor, but would it really drop speed from 1000 to 100?

EDIT: Meant to edit my old post, not post a new one!

---

### Post by Buntumatic on 2011-04-27
Have you tried r8169 driver.

---

### Post by doas777 on 2011-04-27
this:
```

Link partner advertised link modes:  10baseT/Half 10baseT/Full 100baseT/Half 100baseT/Full 

```indicates that your connected device (router/switch) thinks that the link max mode is 100mb/full. that usually means cabling, but it can be switch configuration or a dying switch port. either way, it doesn;t look like the problem is on the ubuntu end from that output.

---

### Post by mmad on 2011-04-27
> **Buntumatic said:**
> Have you tried r8169 driver.

Just tried it, no luck :(.

@doas777 - Perhaps you are right. It's late and I've been tackling this problem for a few hours with no luck. Tomorrow I'll change the cable and see if it helps.

Thanks to everyone who has replied in this thread, I really do appreciate you taking the time to help me out. If I get the problem sorted, I'll be sure to post an update.

---

### Post by mmad on 2011-04-28
> **doas777 said:**
> this:
```

Link partner advertised link modes:  10baseT/Half 10baseT/Full 100baseT/Half 100baseT/Full 

```indicates that your connected device (router/switch) thinks that the link max mode is 100mb/full. that usually means cabling

And you were right! I disconnected the Cat5e cable and stuck in a Cat6e cable I had lying around (it wasn't long enough to go around the walls else I would have used it in the first place) and hey presto it's now connected at 1000mbps! Again thank you to everyone who tried to help me out, its support like this that keeps me using Linux!

---

