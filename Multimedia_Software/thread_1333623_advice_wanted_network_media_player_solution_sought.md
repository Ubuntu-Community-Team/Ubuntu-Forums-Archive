---
title: "advice wanted: network media player solution sought"
date: 2009-11-21
forum: Multimedia Software
---

### Post by kellner on 2009-11-21
I'd appreciate some general advice. I'm looking for a media center (if that's the right word) that works this way: sound and video files are stored on a hard drive that is directly connected to speakers and a tv (well, with cables).  

The thing has a lan interface (or w-lan, doesn't matter). I can mount it locally from an ubuntu or windows desktop via the network, and navigate from my computer, for instance, via itunes. 

What I found so far were network-enabled solutions like the wd tv live (some with the possibility to build in 3.5'' hdds) that did the above, but with one important exception: when they have network abilities, this is to enable these media centers to access data *from* the network (internet or locally). And the only way to navigate through such things is their own proprietary interface, with their own remote control. 

What I'm looking for goes the other way: I want to store stuff on the media center and access it through the network via an interface run from my pc. 

Any advice? We used to have such a setup with an old iMac and a firewire drive (accessed remotely via vnc from the couch if necessary), now the iMac died, and we're looking for a replacement. 

Thanks in advance,

---

### Post by whisky lullaby on 2010-01-15
Maybe you can take EHP-608 network media player for consideration. It's full HD 1080p NMT player and can decode nearly all kinds of formats. :P
For more details, check on its website: [www.elektron-china.com]("http://www.elektron-china.com")

---

### Post by whisky lullaby on 2010-01-15
> **kellner said:**
> 
What I'm looking for goes the other way: I want to store stuff on the media center and access it through the network via an interface run from my pc. 
 
I think it can be reached with EHP-700 which has built-in hard disk. It's just a hard disk to your pc when you connect it to the pc. You can access files to it by whatever you need. So :popcorn: easy.

---

### Post by rossmoore on 2010-01-15
I set up something vaguely similar to what the OP is describing I think. I have a small and silent PC made from a Zotac Ion motherboard. It has a dual atom CPU, Nvidia Ion graphics (i.e. plenty of power for FullHD decoding of H264), ethernet and wifi. It sits next to my TV and my cable modem. It has a huge hard drive with all my media on it.

It connects over PPPoE to the internet, and then shares that connection around the house via wifi (so it acts as the router, dhcp server and wireless access point). I use a wireless mouse/keyboard to play media via my TV / amp+speakers, and randomly browse using my TV as monitor. If I want to access the media via my laptop or another device around the house I can because my media is all on a samba shared drive, accessibl over the wireless network.

Everything is Ubuntu, but my laptop is dual-boot to Vista and that works fine too. Because it's all home-installed I don't end up with any "gotchas" like you have with the wdtv live, which won't let you access the media on your HTPC from elsewhere.

If you want more details of my setup I'm happy to share.

---

### Post by Aat on 2010-01-17
> **whisky lullaby said:**
> Maybe you can take EHP-608 network media player for consideration. It's full HD 1080p NMT player and can decode nearly all kinds of formats. :P
For more details, check on its website: [www.elektron-china.com]("http://www.elektron-china.com")

I am also looking for a media player. This elektron one looks good. I came across another one: [http://dspd.teac.de/index.php?id=4184&L=1](http://dspd.teac.de/index.php?id=4184&L=1)
Both these players work with ext3-formatted HDD's. Does anyone know if this means they will also read ext4?

---

### Post by sports.car.guy on 2010-01-17
I would suggest you just build a low power consuming PC that if it all possible takes advantage of passive cooling. You say how you don't want to have to deal with a lot of work or configuration, well you will probably deal with more getting something like that thing from TEAC. It is cheaply made in comparison to what you can make for the same kind of money if you shop smart. It is a linux machine with wifi.

Now that is something else you do not want to use with streaming of multimedia content. I don't get how these companies can responsibly sell a product that uses a technology like wifi, when the people who developed the software they are using such as MythTV which I am betting TEAC customized, have done extensive testing of it, and it will not provide enough bandwidth using wireless networking. The way wifi works is counterintuitive to streaming multimedia.

Each device connected to a wifi network shares the total bandwidth off of an access point or router. They don't all get a connection as fast as the max of the network like most seem to believe, including obviously TEAC engineers. Not only that the speed the wifi network is rated at is for both transmission and reception of data. Now take into account that each of the devices can set the speed the others negotiate the network at and things can get FUBAR'ed big time.

A b rated wifi card will make an n router or acess point run at the speed the b device is only capable of operating at. In an ideal world that is like 11Mb/s which most HD content is minimum 6Mb/s on average in all honesty and the network is running at 5.5Mb/s in this instance. That is if the wind is right and pigs are flying mind you.

Don't waste your money, because in my opinion this option would be. I would build your own system if I were you with the same cost involved, a few hours of my time, and have something far better with more capabilities.

TEAC is blatantly advertising it running Linux by stating ext2 and ext3 file system capabilities, yet I see nothing about Linux being on the device. Is that not a direct violation of the licensing that it is distributed under with open source?

That right there would be another reason not to purchase the product for me. A lot of people put their blood, sweat, and tears into the software they are packaging on their hardware and not getting credit for it. That is beyond wrong when they have given their code freely to all of us to use. They deserve credit, even if just mentioning each of the software components in a disclaimer.

LG does it in their commercials with Linux based televisions and it is clearly printed in the owner's manual as well. They tell you the version kernel on it even.

---

### Post by Aat on 2010-01-19
> **sports.car.guy said:**
> 
That right there would be another reason not to purchase the product for me. A lot of people put their blood, sweat, and tears into the software they are packaging on their hardware and not getting credit for it. That is beyond wrong when they have given their code freely to all of us to use. They deserve credit, even if just mentioning each of the software components in a disclaimer.

LG does it in their commercials with Linux based televisions and it is clearly printed in the owner's manual as well. They tell you the version kernel on it even.

It's obvious you don't like the TEAC. I for one like the fact that it's running on Linux. I want to encourage them for making a product that supports Linux-systems, by buying one. So my question remains: does anyone know if a player that reads ext3 is also capable of reading ext4?

---

### Post by whisky lullaby on 2010-01-21
As far as i know, EHP-700 and 608 can support ext1, ext2 and ext3. But they have never tried if they can support ext4. Maybe there need to make some practice.:KS

---

