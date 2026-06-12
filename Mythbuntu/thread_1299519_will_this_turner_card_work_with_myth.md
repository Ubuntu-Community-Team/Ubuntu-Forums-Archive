---
title: "will this turner card work with myth"
date: 2009-10-24
forum: Mythbuntu
---

### Post by eliofall on 2009-10-24
does any one know if the ASUS My Cinema-PE9400 card works with mythtv?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815293002]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815293002")

i looked but didnt see it in the wiki. so i'm not sure if if it is suported now or not. 

if its not, can some one point me to a card in the less then 100USD range that is supported and has hardware encoding so theirs not sucks a load on my cpu.

---

### Post by Caysho on 2009-10-24
It is not on the [linuxtv wiki]("http://www.linuxtv.org/wiki/index.php/ASUS"), so I doubt it is supported.
I am using a pair of AVerMedia cards (a777) in my current machine.
Are you after hardware encoding for analogue signals ?  I think you will find that will not be available in a budget card.

---

### Post by eliofall on 2009-10-24
i'm putting together my first HTbox. the card listed above (i mean the Aver-media A188 as i didnt see a A17X) requires 3.0 ghz processor. i just don't want such a heavy load ono the cpu since i will be doing other things on the computer while i'm watching tv. so in my noob way of thinking hardware encoding is a must. 

if am i wrong please tell me. 

is there a tuner card with hardware encoding that works on mythbuntu out of the box? i want to get th card that gives me the least trouble even if i have to pay more for it

---

### Post by fenian on 2009-10-24
A few more details would be helpful...

What is your tv source (i.e: Over the air atsc HDTV ,HDTV cable/satellite,non HDTV cable/satellite)?

What sre your system specs. (processor and graphics card)?

The following is from the Mythtv wiki and may help you in regard to HDTV and hardware encoding...

> 
Digital broadcasting (for DVB and ATSC at least) is in the form of an MPEG-2 transport stream, so unlike analog capture cards, there is no need for any kind of onboard encoding engine, the required program stream is extracted and handed directly to the computer for viewing or saving. Some cards have a hardware Program ID filter (hardware pid) which means the card can extract the required program stream from the transport stream itself.

In either case, the computer power required to save a MPEG-2 transport stream (but not view it) is very small, being only what is required to shift data from the PCI/USB bus and save it to disk.

Confusingly, many useful tools for working with MPEG-2 transport streams have "dvb" in their names, even though they work just as well with MPEG-2 transport streams derived from "ATSC" broadcasts.

Some digital capture cards also support analog (NTSC or PAL) transmissions, usually via a frame grabber. If your digital capture card lacks such hardware and you want to record both digital and analog transmissions, you'll need to buy a separate analog capture card - either a frame grabber or a hardware-encoding card.

With the world moving towards digital broadcast standards, this type of card is likely to become dominant in the next few years. 

---

### Post by fenian on 2009-10-24
[This card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116033") is simliar to the one you listed and works with Mythbuntu.Note that the hardware encoder only works with NTSC (analog) signals and in the U.S. and many other regions all over the air signals are digital (ATSC/DVB) if you have a cable/satellite set top box you may be able to use the composite or s-video output to capture tv.

---

### Post by eliofall on 2009-10-24
i'm specs...
cpu:  intel 3.0ghz FSB: 1333
video card: geforce 9800 gtx+
ram: 2gigs

i am wanting the card for cable(suddenlink) i guess thats not HD but really i dont know.

i am seeing some cards that you can record on one channel and watch another or picture in picture. is that supported in mythbuntu? and do the cards wor out of the box or is it like the wireless cards were 2 years ago when you had to take the windows driver and use a program to convert it and install it?( my first ubuntu install was a tiresome work to get everything working)

---

### Post by eliofall on 2009-10-24
double post....

---

### Post by fenian on 2009-10-24
The card I linked to above can hook up to a cable box to grab the NTSC signal through a s-video input and a composite audio input or  through one of the coaxial inputs (the other is for HDTV),in this setup it would use the hardware encoding chip.In order to watch one channel and record another you need two sources (two cable boxes) and  a second card card.

---

### Post by eliofall on 2009-10-25
ok thanx. i will go with the Hauppauge WinTV-HVR1600 card. i dont have a cable box so i will have to do some looking around to find the best way to have two inputs. maybe i could get a vcr or something and run an s cable from it for another input... well i have some googling to do. 

thanx guys

---

