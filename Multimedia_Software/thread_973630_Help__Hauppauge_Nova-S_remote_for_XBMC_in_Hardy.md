---
title: "Help:  Hauppauge Nova-S remote for XBMC in Hardy"
date: 2008-11-06
forum: Multimedia Software
---

### Post by chene on 2008-11-06
Greetings,

I've been using XBMC Beta 2 in Ubuntu Hardy (8.0.4) since it was released. Coming from a modded xbox-1 with xbmc I must say it is great to have it working under linux. My old xbox just couldn't decode 720p and xbmc for linux solves this problem.

So far I've tweaked XBMC to my liking, except for the remote.

I have a Hauppauge Nova-S DVB-S card with a remote. Most of the buttons works with the default xbmc setting except for a few. I thought I'd follow the guide at the sticky: [http://xbmc.org/forum/showthread.php?t=39183](http://xbmc.org/forum/showthread.php?t=39183), but I've encountered some problems. It looks like the customized Lircmap.xml I have in ~/.xbmc/userdata is not been loaded. I seek your help.

First of, I'm using the following:
/etc/lirc/lircd.conf (this is actually taken from mythtv's wiki: [http://www.mythtv.org/wiki/index.php...ova-S_Plus_PCI](http://www.mythtv.org/wiki/index.php...ova-S_Plus_PCI))

```

begin remote

name hauppauge_nova-s
bits 16
eps 30
aeps 100

one 0 0
zero 0 0
pre_data_bits 16
pre_data 0x8001
gap 132844
toggle_bit 0

begin codes
Go 0x0161
Power 0x0074
TV 0x0179
Videos 0x0189
Music 0x0188
Pictures 0x016F
Guide 0x016D
Radio 0x0181
UP 0x0067
LEFT 0x0069
RIGHT 0x006A
DOWN 0x006C
OK 0x001C
Back 0x00AE
Menu 0x008B
Vol+ 0x0073
Vol- 0x0072
CH+ 0x0192
CH- 0x0193
Prev-Ch 0x019C
Mute 0x0071
Rec 0x00A7
Stop 0x0080
FRW 0x00A8
Play 0x00CF
FFW 0x00D0
Skip-Back 0x00A5
Pause 0x0077
Skip-For 0x00A3
1 0x004F
2 0x0050
3 0x0051
4 0x004B
5 0x004C
6 0x004D
7 0x0047
8 0x0048
9 0x0049
Star 0x0184
0 0x0052
Hash 0x0172
Red 0x018E
Green 0x018F
Yellow 0x0190
Blue 0x0191
end codes

end remote

```

I then grab a copy of the default Lircmap.xml into my personal xbmc directory:
```

cp /usr/share/xbmc/system/Lircmap.xml ~/.xbmc/userdata/

```

and added a section for hauppauge_nova-s
```

<lircmap>
	<remote device="hauppauge_nova-s">
		<left>LEFT</left>
		<right>RIGHT</right>
		<up>UP</up>
		<down>DOWN</down> 
		<select>OK</select>
		<back>Back</back>
		<menu>Menu</menu>
		<info>guide</info>
		<display>Go</display> 
		<title>Prev-Ch</title>
		<play>Play</play>
		<pause>Pause</pause>
		<reverse>FRW</reverse>
		<forward>FFW</forward>
		<skipplus>Skip-For</skipplus>
		<skipminus>Skip-Back</skipminus>
		<stop>Stop</stop>
		<zero>0</zero>
		<one>1</one>
		<two>2</two>
		<three>3</three>
		<four>4</four>
		<five>5</five>
		<six>6</six>
		<seven>7</seven>
		<eight>8</eight>
		<nine>9</nine>
		<power>Power</power>
		<myTV>TV</myTV>
		<mymusic>Music</mymusic>
		<mypictures>Pictures</mypictures>
		<myvideo>Videos</myvideo> 
		<record>Rec</record>
		<start>Green</start>
		<volumeplus>Vol+</volumeplus>
		<volumeminus>Vol-</volumeminus>
		<channelplus>CH+</channelplus>
		<channelminus>CH-</channelminus>
		<pageplus>Blue</pageplus>
		<pageminus>Yellow</pageminus> 
		<mute>Mute</mute>
		<star>Star</star> 
		<hash>Hash</hash>
		<clear>Red</clear>
	</remote>
</lircmap>

```

I didn't change the default Keymap.xml.


My questions are:

1) Is there any other configuration that needs to be changed?
2) is there a program that double-checks the lircmap.xml to make sure all the tags are properly formatted?
3) I noticed that under my ubuntu hardy (32bit), the event number associated with the remote changes everytime it is booted. Will this affect anything?
4) According to the sticky at XBMC's forum, the file names under ~/.xbmc/userdata should be **l**ircd.conf instead of the **L**ircd.conf. I've tried both but still couldn't get buttons such as myvideo to work. Which one should it be? 

At this point, it looks like my customized Lircmap.xml isn't being loaded. I would appreciate any help is getting this to work; trying to make sure I wrote a proper XML file by hand is hard

Thanks in advance,

---

### Post by chene on 2008-11-09
can anyone please help?  I've posted this message at xbmc.org and has not gotten replies either.

Thanks,

---

### Post by aidans on 2008-11-15
I have the same problem with a Hauppage_350. I've configured Lirc properly, and xbmc.log shows the keys going in but nothing actually happens...

---

### Post by aidans on 2008-11-15
Durr, ok. Lircmap.xml has to be ~/.xbmc/userdata the one in /usr is ignored.

---

