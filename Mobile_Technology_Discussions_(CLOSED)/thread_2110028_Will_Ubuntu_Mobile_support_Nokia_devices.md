---
title: "Will Ubuntu Mobile support Nokia devices?"
date: 2013-01-29
forum: Mobile Technology Discussions (CLOSED)
---

### Post by scaramoosh on 2013-01-29
I have a Nokia 808 because I'm an idiot and I am locked into it for 2 years on contract and desperately need something other than Symbian. I dunno what I was expecting from the phone, I love the camera and expected and OS that functioned, sadly it is like using a phone from 10 years ago. 

Please tell me there will be support for Nokia devices as I believe Symbian is an open platform.... that or Nokia's security is as bad as the rest of the OS.

---

### Post by josephmills on 2013-01-30
Qt/qml(owned by nokia and the phones front end) supports 

linux embed devices 
blackberry 
meegoo 

> When it comes to your app's UI, the declarative, JavaScript-like QML language within Qt Quick and tools such as Qt Quick Components enable you to create compelling UIs faster than you thought possible. And better still, you only need one core code-base to address the 180 million Qt-powered Symbian and Nokia N9 phones in consumers hands today. Qt enables code reuse that allows you to build and deploy versions of your apps for desktop platforms too.[1] 

[1] [http://www.developer.nokia.com/Develop/Qt/](http://www.developer.nokia.com/Develop/Qt/)

---

### Post by 3rdalbum on 2013-01-30
No, Ubuntu for Smartphones is intended as an operating system to be preinstalled on phones, not as one that can be installed on an existing phone

The development phone is the Nexus S, that's the only phone that will be able to be retrofitted with Ubuntu.

---

### Post by Danny1234 on 2013-02-01
I am afraid you cannot do that although there are the application Ubuntu for phones.

---

### Post by jhoninck on 2013-02-02
Have owned a Samsung Galaxy, was not impressed by the hardware quality.
Actually I am a die hard fan of the Nokia hardware, my three year old E71 never fails.

Would like to upgrade to a new Nokia, but never in my life will it be to a Windoze phone.
Is there any chance of getting ubuntu running on recent Nokia phones ??

If FirefoxOS is possible, then also ubuntu  ?
[http://www.youtube.com/watch?v=jdXfStB2dQ0](http://www.youtube.com/watch?v=jdXfStB2dQ0)

Any working instructions are more than welcome, the 920 is the top phone as far as hardware is concerned.

---

### Post by whatthefunk on 2013-02-02
Wrong thread...  Mods please delete

---

### Post by Nr90 on 2013-02-02
> **3rdalbum said:**
> No, Ubuntu for Smartphones is intended as an operating system to be preinstalled on phones, not as one that can be installed on an existing phone

The development phone is the Nexus S, that's the only phone that will be able to be retrofitted with Ubuntu.

From what are you drawing this conclusion?

Canonical will start by providing a rom for the galaxy nexus (not nexus S).
However the source will also be open. So why wouldn't your phone dev be able to port it to your handset?

Don't know if porting to the nokia 808 is possible, since it's not android.

---

### Post by 3rdalbum on 2013-02-02
> **Nr90 said:**
> From what are you drawing this conclusion?

Canonical will start by providing a rom for the galaxy nexus (not nexus S).
However the source will also be open. So why wouldn't your phone dev be able to port it to your handset?

Don't know if porting to the nokia 808 is possible, since it's not android.

Porting might be possible, but it will not be supported officially as far as anyone knows.

---

### Post by ugm6hr on 2013-02-03
> **Nr90 said:**
> Don't know if porting to the nokia 808 is possible, since it's not android.

The reason all the "new" phone OS use Android stack as a base is to ensure drivers are available for the various components. So it really depends on what components Nokia selected. Essentially, if Android is ported to your phone (unlikely), then Ubuntu may also be technically possible.

As an example, even my relatively popular (but now aged and redundant) Windows PDA (Dell Axim 51x) never got beyond very superficial functioning on Android due to lack of driver support.

---

### Post by ugm6hr on 2013-02-03
The N9 is (was) a MeeGo (i.e. Linux) phone, and installing Ubuntu / Firefox OS is dependent on an underlying Android stack (which is available for N9 as nitdroid).

It really depends on whether the hardware components in Nokia phones have the drivers necessary to run Android. 

And whether anyone who buys a Windows phone today will have the inclination to develop an Android port (unlikely).

---

### Post by m3topaz on 2013-02-05
I'm a die-hard Nokia fan. Or rather I used to be - my N9 is the last Nokia I'll ever buy. Or they drop Windows Phone and make something (anything!) else.
I think the days where Nokia make the best hardware are coming to an end, sadly. The Windows Phones from Nokia are a step behind the best Symbian and Linux phones, it's probably the end of the road for them in smartphones.
Hang on and see if Jolla get anything high-end out, I suggest.

---

### Post by scaramoosh on 2013-02-07
They're all ARM based anyways ain't they? I thought Mobiles all had the same hardware in them these days. The 808 uses and ARM CPU and Broadcom GPU....... gotta be pretty common drivers you can pack into the OS as standard.

---

### Post by scaramoosh on 2013-02-07
The 808 is my first Nokia mobile and Symbian is great, I prefer it to IOS, the only thing it lacks is apps. Sadly since Nokia have ditched Symbian I need Ubuntu or something with the potential to have great app support.

Shame really cause Windows Phone is ****.

---

### Post by mörgæs on 2013-02-07
Threads merged.

---

### Post by 3rdalbum on 2013-02-07
> **scaramoosh said:**
> They're all ARM based anyways ain't they? I thought Mobiles all had the same hardware in them these days. The 808 uses and ARM CPU and Broadcom GPU....... gotta be pretty common drivers you can pack into the OS as standard.

No, there are several different SoCs used in phones, and a wide array of different GPUs which mostly don't have X drivers, only Android display drivers.

---

