---
title: "TV Tuner recommendations"
date: 2009-02-02
forum: Mythbuntu
---

### Post by Hehaub on 2009-02-02
I am almost ready to build my first HTPC. I have seen alot of comflicting/outdated/etc information around the net and I wanted to get some feedback before I selected my tuner. Here is my situation...

I am in Indiana,USA. I would like to pick up my digital terrestrial broadcasts mainly. I would like to eventually pickup/record from Dish Network(I currently have a STB DVR from them). I have a Freebsd file server that currently holds my video/music/pics. I plan to have my mythbox connect to this for media. HD is not important, but analog is going away here in the US Feb.19th. I would like to be able to record one channel while watching another.

I am a bit uncertain which TV card would work best for my situation.
Supported hardware - IVTV makes it seem as though alot of the cards I see on Amazon are not supported. Here are a couple that seem to fit what I need:

[[COLOR="Red"]hd_5500[/COLOR]](http://www.pchdtv.com/hd_5500.html)
[[COLOR="Red"]WinTV-HVR-1250 Product overview[/COLOR]](http://www.hauppauge.com/site/products/data_hvr1250.html)

I have Mythbuntu installed on a spare PC here(testing) and I have thrown some video/audio/images on it. It seems to be a good fit for what I would like to do.

Thoughts/suggestions?

Thanks,
Hehaub

---

### Post by cchester on 2009-02-02
Hey,

Don't know if this helps but I have a Hauppage PVR150 analog that works great but does one recording at a time but from what I understand  you can have two but you just need to set both up seperately to work with myth.

The drivers work great with myth and I have had no problems. You should be able to find one cheap or two on the net. That is where I got mine.

The biggest thing I remember about the tuner cards is just making sure you get one with the right chip because some cards even if they seem supported if the chip is wrong then your out of luck in getting it to work. So make sure the chip on the card you pick is supported and make sure it does hardware encoding and decoding and it doesn't use software to do it as well.

Hope this helps.

---

### Post by newlinux on 2009-02-02
pci or pci-e? Or networked (hdhomerun is a networked dual digital tuner)

The pvr-150 won't work for your digital OTA broadcasts (ATSC).

A good place to start looking:
[http://www.linuxtv.org/wiki/index.php/ATSC_Devices](http://www.linuxtv.org/wiki/index.php/ATSC_Devices)

You can also take a look at the hardware thread here to see what people are using. I have 3 different cards that can tune ATSC (kworld 110/115, avermedia A180, and dvico fusion 5 lite). All of those are PCI and harder to find these days. I've used a pchdtv 5500 and it will do what you want. With one card you'll be able to record two things at once only on station on the same multiplex. otherwise you'll need two cards to watch one thing and record another at the same time. The hdhomerun has two tuners built in for doing this.

---

### Post by Hehaub on 2009-02-02
It can be PCI or PCI-E, I am going to be buying/building a system, so I want to make sure everything is compatible before I move forward. I don't see a need to get a card with analog capabilities since the analog signal in my area will be gone in just a couple weeks. I like the idea of a dual tuner on a single card more than two separate cards. I am still in data collection mode. That HDHomerun unit just blew my mind, I didn't know that existed. I will have to look into that further! Thanks for the linkage!

---

### Post by bryanf2009 on 2009-02-02
List of TV Cards:  [http://www.mythtv.org/wiki/Video_capture_card](http://www.mythtv.org/wiki/Video_capture_card)

Problem is I have the Twinhan AD-SP300 (1034) and I cannot seem to get MythBuntu to recognise the card.

[http://www.linuxtv.org/wiki/index.php/DVB-T_Devices](http://www.linuxtv.org/wiki/index.php/DVB-T_Devices)
[http://www.linuxtv.org/wiki/index.php/DVB-S_PCI_Cards](http://www.linuxtv.org/wiki/index.php/DVB-S_PCI_Cards)
[http://www.linuxtv.org/wiki/index.php/DVB-S2_Devices](http://www.linuxtv.org/wiki/index.php/DVB-S2_Devices)

Bryan

---

### Post by mikeklein on 2009-02-04
hdhomerun all the way.

Dual dtv/qam tuners (assignable in any way) hooked up to an ethernet port.

Cost is around $140.

---

### Post by bwooster0 on 2009-02-12
Just get the hdhomerun. You will need to hook two antenna wires up to it but it just works. The hdhomerun also works with, Windows XP, Vista, Mac OS and linux. The hdhomerun does NOT come with a remote control so if you want to use one with your Mythbox you need to find another solution for that issue.

I have a little linksys router (flashed to run ddw-rt) that has the mythbox and the hdhomerun hooked up to it so that the network traffic when recording does not affect the (wireless) network thru my house.

I also have a DVICO HDTV7 Dual Express which I just put into my Mythbox. It is a dual tuner that only requires one cable to be attached to it, that is a nice feature. I wrote in another thread about how I set it up to work with Mythtv. I have not tried to use the remote that it came with since I have an old ATI RF remote that is working fine. You nned to make sure that the motherboard you use has a PCIE slot for the card.

If you can use a motherboard that has the nvidia 9300 or 9400 chipset (~$110) with an HDMI output then you won't need to buy a video card at all. It would save on energy too since you won't need to power a video card.

---

