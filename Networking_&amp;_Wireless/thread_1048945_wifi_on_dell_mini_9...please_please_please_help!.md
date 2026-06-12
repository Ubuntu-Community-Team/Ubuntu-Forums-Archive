---
title: "wifi on dell mini 9...please please please help!"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by makegreenbygoinggreen.com on 2009-01-24
[FONT="Comic Sans MS"][COLOR="SeaGreen"]I have a new white dell mini 9.

Here is what I was looking to accomplish:

I wanted to be able to get to one single website, and no matter what the location. So At & t told me I needed a wireless card. It plugs right into the usb port. However, from my understanding there is some sort of set up needed to be able to use it.

At & t could not help me. They referred me to Sierra wireless.
Sierra wireless could not help me. They referred me to Dell.
Dell could not help me. They referred me to Ubuntu.
Ubuntu wants to charge me $ 250- bucks to give me the instructions on how to set up the wifi.

Just can't afford it. So I look to this forum for help. I hope someone can help me.

What you should know:

I guess I'm somewhat computer illiterate. I've always had and have Macs, and I guess I've gotten use to everything booting itself. However, from my understanding with my dell mini 9, I need to program something-?

At & t seems to think that my wifi should plug in and simply work, but it does not.

I'm on month 2 of a 2 year contract for my wi-fi and still have not been able to use it.

I'm so upset.....can you help me-?

Blessings, M [-o<[/COLOR][/FONT]

makegreenbygoinggreen.com
soap-mart.com

---

### Post by zenial on 2009-01-24
Wow "mac user really"
mac has limitations
ubuntu has none
...
Okay so what are ur specifications?

---

### Post by makegreenbygoinggreen.com on 2009-01-24
Wow "mac user really"
mac has limitations
ubuntu has none
...
Okay so what are ur specifications?
__________________
I WANT TO LEARN IT ALL!! 

[FONT="Comic Sans MS"][COLOR="SeaGreen"]That's what everyone says, but I rarely have problems. Everyone always tells me to go pc. I was told to go Dell mini 9 so I did. But for one simple little thing I'm looking to do and paying through the nose for, I can't even do. Honestly, I feel like crying. Gosh!

I'm not sure what you mean what are my specifications-?

I have a dell mini 9 w/8 mb or gb not sure. I know that is was more than the 4 it came with so it cost a little extra. I was told meaning that I had more space and it would run quicker. I only want to get to one website and anywhere. That's it. I have an at + t usb card. They say I only have to plug it in and it works. Maybe it does, but I don't know how I'm supposed to know that. Am I supposed to program something for it to work. They were trying to go step by step with me on the phone but it was supposed to load something on my computer, after plugging in, but it never did.

??? I don't have any clue what to do. M.[/COLOR][/FONT]

---

### Post by pytheas22 on 2009-01-24
It should not be too much work to get this going.  Please plug the wireless card that AT&T gave you into your computer, then open a terminal from the Applications>Accessories menu (or it may be in a different location; I think the Dell Minis have a customized interface).  Run these commands (one per line) and post the output here:
```

lsusb
lshw -C Network
sudo iwlist scan
```

That will give us the information we need in order to tell you how to set the card up.

It would also be good if you told us the name of the wireless card, which is probably printed on it somewhere.  Is the model number something like 881U?

---

### Post by makegreenbygoinggreen.com on 2009-01-24
[COLOR="SeaGreen"][FONT="Comic Sans MS"]Ok. I will get all this info tomorrow.[/FONT]

[FONT="Comic Sans MS"]The card is from At & t but when I needed help they told me to contact sierra wireless. So I guess they are one in the same-?

I will do this tomorrow morning and post the reply after following your instructions.

I would do it now but I can barely see this computer screen. Been on it all day looking for answers.

Thanks so much for your reply. I truly appreciate it~! M.[/FONT][/COLOR]

---

