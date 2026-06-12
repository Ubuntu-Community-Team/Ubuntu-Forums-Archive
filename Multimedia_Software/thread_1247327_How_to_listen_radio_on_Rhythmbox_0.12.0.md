---
title: "How to listen radio on Rhythmbox 0.12.0?"
date: 2009-08-22
forum: Multimedia Software
---

### Post by vickoxy on 2009-08-22
Hi, 
wanted to use Rhythmbox 0.12.0 as radio station center, but every station i add (http adress) ends with  error. Is there any easy way to make Rhythmbox 0.12.0 to work with my Ubuntu 9.04?
Thanks

I installed some packages (think mmcO text2html-but no change.

---

### Post by vickoxy on 2009-08-30
I can not add this radio to my rhythmbox (or some mms stations):

[http://wien.orf.at/magazin/studio/radiowien/popup?skin=liveradio2](http://wien.orf.at/magazin/studio/radiowien/popup?skin=liveradio2)

But if the adress ends on **.m3u**, then everything works fine. Does anyone knows what do i have to install to make those radio-stations to work?

---

### Post by ron999 on 2009-08-30
Hi
I'm still using Rhythmbox v0.10.0
That radio station you linked is working OK for me.
In Rhythmbox choose 'New internet radio station'.
Then paste this as the url:-
```
mms://apasf.apa.at/radio_wien_worldwide
```

The http links that you tried are links to the webpage.
You have to dig deeper to find the link to the radio feed.

---

### Post by vickoxy on 2009-08-31
> **ron999 said:**
> Hi
I'm still using Rhythmbox v0.10.0
That radio station you linked is working OK for me.
In Rhythmbox choose 'New internet radio station'.
Then paste this as the url:-
```
mms://apasf.apa.at/radio_wien_worldwide
```

The http links that you tried are links to the webpage.
You have to dig deeper to find the link to the radio feed.

Thanks-i figured that also-found the same station with "Web Site Infos".
Still, some are played in browser but some can i not play:
[http://www.radio101.hr/](http://www.radio101.hr/) (can not play in browser)
[http://www.hrt.hr/stream/PROGRAM2](http://www.hrt.hr/stream/PROGRAM2) (this one i can play in browser but not in rhythmbox)

Just wanted to know are there some codecs i should install ore how it is working...

---

### Post by ron999 on 2009-08-31
> **vickoxy said:**
> also-found the same station with "Web Site Infos".

^  ^  ^
This is correct.

The other two stations.
radio101
This won't play in my browser but asks to open 'Totem'.
The link for Rhythmbox is
```
mms:media.t-com.hr/101

```

croatian radio PROGRAM2
This one is too difficult.
It plays using 'flash'.
There is no link for Rhythmbox to use.
Many stations use this method. :sad: :frown:
But dig deeper and deeper, sometimes there is an extra feed for iPhones.

Some radio stations offer several feeds. Low-quality for dial-up, high-quality for broadband.
Here are two high-quality feeds.
RadioParadise.com
```
http://scfire-dtc-aa01.stream.aol.com/stream/1049
```
RadioCaroline.co.uk
```
http://sc1.abacast.com:8105/
```
:guitar:

---

### Post by vickoxy on 2009-08-31
> **ron999 said:**
> ^  ^  ^
This is correct.

The other two stations.
radio101
This won't play in my browser but asks to open 'Totem'.
The link for Rhythmbox is
```
mms:media.t-com.hr/101

```

croatian radio PROGRAM2
This one is too difficult.
It plays using 'flash'.
There is no link for Rhythmbox to use.
Many stations use this method. :sad: :frown:
But dig deeper and deeper, sometimes there is an extra feed for iPhones.

Some radio stations offer several feeds. Low-quality for dial-up, high-quality for broadband.
Here are two high-quality feeds.
RadioParadise.com
```
http://scfire-dtc-aa01.stream.aol.com/stream/1049
```
RadioCaroline.co.uk
```
http://sc1.abacast.com:8105/
```
:guitar:

Thanks for your answers. Well i can live whitout some stations. Still ```
mms:media.t-com.hr/101

``` couldn´t get to work-any idea?

---

### Post by vickoxy on 2009-08-31
Well ron999, you gave me just good idea-your stations seems good for me.

So, if someone can suggest me more good jazz/blues/ or rock stations...

Thanks

---

### Post by ron999 on 2009-09-01
> **vickoxy said:**
> Still ```
mms:media.t-com.hr/101

``` couldn´t get to work-any idea?
Yes, my bad. :redface:
This is the correct link:-
```
http://media.t-com.hr/101
```

---

### Post by vickoxy on 2009-09-01
> **ron999 said:**
> Yes, my bad. :redface:
This is the correct link:-
```
http://media.t-com.hr/101
```

Thank you very much!

---

