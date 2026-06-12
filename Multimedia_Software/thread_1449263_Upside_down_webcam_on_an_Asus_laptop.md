---
title: "Upside down webcam on an Asus laptop"
date: 2010-04-07
forum: Multimedia Software
---

### Post by Mark.arted on 2010-04-07
Hi everyone, I'm an Ubuntu newbie. I like it overall, but am still getting used to working differently than I have for the past 20 years with windows.
Can anyone tell me how to best fix an upside down webcam image? I have an Asus G50 VT-X5 and I am using Ubuntu 9.10
I called Asus and they are as ignorant as I regarding Linux, but they did tell me that I have either a Chiconi or a Suyin built-in webcam.

---

### Post by no2498 on 2010-04-07
did you try to flip the pic in cheese
it should help in all things to do with the cam
cheese is to have all the settings for webcams

---

### Post by Chris Musampa on 2010-04-07
I have a K70IO with suyin webcam, the intructions in this link are straightforward and work for me:
[http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/](http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/)

---

### Post by Mark.arted on 2010-04-07
> **no2498 said:**
> did you try to flip the pic in cheese
it should help in all things to do with the cam
cheese is to have all the settings for webcams
Yes, it does flip in Cheese, but there seems to be no flip function in skype. People who receive my image see it upside down as well.

---

### Post by Mark.arted on 2010-04-07
> **Chris Musampa said:**
> I have a K70IO with suyin webcam, the intructions in this link are straightforward and work for me:
[http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/](http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/)
Thanks, I'll give it a try.

---

### Post by Mark.arted on 2010-04-07
I appreciate the effort Chris, but as a linux newbie, I have no idea what a wrapper is.
Anything a little more entry level out there?

Cheers.

---

### Post by Chris Musampa on 2010-04-08
> **Mark.arted said:**
> I appreciate the effort Chris, but as a linux newbie, I have no idea what a wrapper is.
Anything a little more entry level out there?

Cheers.
Hi Mark, you don't say what cam app you're using but for example if you were using Kopete you could edit the menu entry (I don't know how in ubuntu as I'm a kubuntu user) to become:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so kopete

---

### Post by Mark.arted on 2010-04-08
Hi Chris. My main concern is getting Skype to work with a rightside up image. I want to be able to read to my niece and nephew who live eight hours away and I'd like them to get a correct image so I can easily show them the book I'm reading.

I went into the details for installing a PPA then installed the libv4l-0 package.

Then I took a chance and entered 
[COLOR=#7A0874]**echo**[/COLOR] [COLOR=#660033]-e[/COLOR] [COLOR=#FF0000]"[COLOR=#000099]**\n**[/COLOR]# libv4l PPA[COLOR=#000099]**\n**[/COLOR]deb [http://ppa.launchpad.net/libv4l/ppa/ubuntu](http://ppa.launchpad.net/libv4l/ppa/ubuntu) [COLOR=#780078]`lsb_release -c | awk '{print $2}'`[/COLOR] main"[/COLOR] [COLOR=#000000]**|**[/COLOR] [COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**tee**[/COLOR] [COLOR=#660033]-a[/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]apt[COLOR=#000000]**/**[/COLOR]sources.list
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-key**[/COLOR] adv [COLOR=#660033]--recv-keys[/COLOR] [COLOR=#660033]--keyserver[/COLOR] keyserver.ubuntu.com C3FFB4AA
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get**[/COLOR] update
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get**[/COLOR] [COLOR=#C20CB9]**install**[/COLOR] libv4l-[COLOR=#000000]0

into my terminal although that wasn't specified as an action I should take.
After doing that my image in Cheese is upright as it should be!

So far so good, but the image is still upside down in Skype.

Mark
[/COLOR]

---

### Post by no2498 on 2010-04-08
get a hold of the cheese ppl
they have all the settings for the webcams they/ubuntu give it to them

good luck

---

### Post by Martijn. on 2010-04-15
Hi you all,
I have the same problem on my Asus laptop with a built in webcam. Using Linux 9.10 and Skype for Linux 32bits. If there is a solution found it would be great.
Rgds,
Martijn

---

### Post by Chris Musampa on 2010-04-15
> **Mark.arted said:**
> Hi Chris. My main concern is getting Skype to work with a rightside up image. I want to be able to read to my niece and nephew who live eight hours away and I'd like them to get a correct image so I can easily show them the book I'm reading.

I went into the details for installing a PPA then installed the libv4l-0 package.

Then I took a chance and entered 
[COLOR=#7A0874]**echo**[/COLOR] [COLOR=#660033]-e[/COLOR] [COLOR=#FF0000]"[COLOR=#000099]**\n**[/COLOR]# libv4l PPA[COLOR=#000099]**\n**[/COLOR]deb [http://ppa.launchpad.net/libv4l/ppa/ubuntu](http://ppa.launchpad.net/libv4l/ppa/ubuntu) [COLOR=#780078]`lsb_release -c | awk '{print $2}'`[/COLOR] main"[/COLOR] [COLOR=#000000]**|**[/COLOR] [COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**tee**[/COLOR] [COLOR=#660033]-a[/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]apt[COLOR=#000000]**/**[/COLOR]sources.list
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-key**[/COLOR] adv [COLOR=#660033]--recv-keys[/COLOR] [COLOR=#660033]--keyserver[/COLOR] keyserver.ubuntu.com C3FFB4AA
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get**[/COLOR] update
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**apt-get**[/COLOR] [COLOR=#C20CB9]**install**[/COLOR] libv4l-[COLOR=#000000]0

into my terminal although that wasn't specified as an action I should take.
After doing that my image in Cheese is upright as it should be!

So far so good, but the image is still upside down in Skype.

Mark
[/COLOR]

Sounds like the modified library installed OK, try starting skype like this in terminal:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

If that fails I can't help any further as this is what works for me (with Kopete rather than Skype).

---

### Post by rsumy on 2010-06-12
**Ubuntu upside down webcam**:

**gtk-v4l**:
```
sudo add-apt-repository ppa:libv4l
```
```
sudo aptitude update && sudo aptitude install gtk-v4l libv4l-0
```

*Applications > Sound & Video > Video4Linux Device Preferences (**= gtk-v4l**)*:

[[IMG]http://i.imgur.com/0MOBfs.jpg[/IMG]](http://i.imgur.com/0MOBf.png)

**Vflip** = Vertical Flip... :).

rsumy

---

### Post by szirakitamas on 2010-06-20
Hi,
Yesterday I have installed 10.04 on an Asus F3E series laptop of a friend with a Bus 001 Device 002: ID 174f:5a35 Syntek Sonix 1.3MPixel USB 2.0 Camera. The camera in Skype installed from partner repo (just as the other 2.1.0.81 version for Karmic Koala and so) does not seem to work. The led lights but no image. Sometimes had image but it was frozen, and upside down. Tried older version of Skype (2.0.0.72 and 2.1.0.47), and the camera works correctly except the upside-down image. But this problem could be solved by installing the above mention libv4l-0 package from the Launchpad PPA. So everyone is happy!
Bests,
T

---

### Post by techieboy on 2010-08-08
Hello!

I tried reading several threads and articles online to fix my inverted webcam on my asus k52j laptop. After several days of looking for a solution... I finally had a solution!

the trick is just to install libv4l-0 and export LIBV4LCONTROL_FLAGS upon running the app. It works on my cheese and skype... 

I wrote an article about this on my blog... try reading my article on [http://techieboycdo.blogspot.com/2010/08/fix-upside-down-or-inverted-webcam-on.html](http://techieboycdo.blogspot.com/2010/08/fix-upside-down-or-inverted-webcam-on.html)

Have a good one! And thanks to this thread...

---

### Post by mavka13 on 2010-09-27
That's just great! Thank you a lot! This solution finally worked for me!

The only thing was that in my case the LIBV4LCONTROL_FLAGS should have been 1 to produce the right picture:

$export LIBV4LCONTROL_FLAGS=1 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

---

### Post by misosofos on 2010-11-01
I can't solve the webcam issue. After installation am I supposed to be able to run gtk-v42 like a command? 

I have another laptop, but identical issue about webcam upside down image. Is there any deb package to install gtk-v42?


*Edited: sorry, my fault. I was reading two threads and I didn't see the package in this one. Thank you!

---

### Post by hamidrjafari on 2011-04-08
It took me a good time :) but at last,

Thanks to techieboy:

"the trick is just to install libv4l-0 and export LIBV4LCONTROL_FLAGS upon running the app. "

Also others providing the library and assistance and ...

---

### Post by Coobuntu on 2012-01-08
> **techieboy said:**
> Hello!

I tried reading several threads and articles online to fix my inverted webcam on my asus k52j laptop. After several days of looking for a solution... I finally had a solution!

the trick is just to install libv4l-0 and export LIBV4LCONTROL_FLAGS upon running the app. It works on my cheese and skype... 

I wrote an article about this on my blog... try reading my article on [http://techieboycdo.blogspot.com/2010/08/fix-upside-down-or-inverted-webcam-on.html](http://techieboycdo.blogspot.com/2010/08/fix-upside-down-or-inverted-webcam-on.html)

Have a good one! And thanks to this thread...
Thanks buddy, your solution is the only one that heped me out after doing research for months and being fed up. I highly recommend it! I run Ubuntu (10.04) Lucid Lynx 64 bit OS version on my Asus K52JU.

BTW, it was me the one who post in your article earlier today, but I changed some settings and it even worked for my Gmail. So for those who need a solution for Google Talk, this works too.  

Greetings to everyone!

---

### Post by raffalaser on 2012-01-15
> **techieboy said:**
> Hello!

I tried reading several threads and articles online to fix my inverted webcam on my asus k52j laptop. After several days of looking for a solution... I finally had a solution!

the trick is just to install libv4l-0 and export LIBV4LCONTROL_FLAGS upon running the app. It works on my cheese and skype... 

I wrote an article about this on my blog... try reading my article on [http://techieboycdo.blogspot.com/2010/08/fix-upside-down-or-inverted-webcam-on.html](http://techieboycdo.blogspot.com/2010/08/fix-upside-down-or-inverted-webcam-on.html)

Have a good one! And thanks to this thread...

hi all, on my 11.04 this is working only with cheese....skype still have upside down image...
actually i am using skype beta 2.2, and i have tried

export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

with value 1, 2 and 3.....sigh sigh....this is what coming

raffalap@raffa:~$ $export LIBV4LCONTROL_FLAGS=1 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
LIBV4LCONTROL_FLAGS=1: command not found
raffalap@raffa:~$ export LIBV4LCONTROL_FLAGS=2 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
Corrupt JPEG data: 39 extraneous bytes before marker 0xd9
raffalap@raffa:~$ export LIBV4LCONTROL_FLAGS=3 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
Corrupt JPEG data: 39 extraneous bytes before marker 0xd9
raffalap@raffa:~$ 


plsplspls if somebody get something in mind help out:shock:

forgot to mention....i have an Asus U31J laptop....

---

