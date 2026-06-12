---
title: "X86 support of Tablet OS?"
date: 2013-02-22
forum: Mobile Technology Discussions (CLOSED)
---

### Post by swanlee on 2013-02-22
Looking at the current support for the Tablet OS dev preview looks like only arm based android devices are supported.

I have an older X86 Win7 tablet I'd like to put the Ubuntu Tablet OS on. Is this going to be possible when they are closer to release?

---

### Post by grahammechanical on 2013-02-22
I am not meaning to be funny but Ubuntu is already available for Intel x86 CPUs. It is Ubuntu desktop AMD64 or i386.

As I understand Canonical's convergence strategy many of the features of Ubuntu Touch will be available in the images for Ubuntu desktop. We should not think of Canonical developing 3 or 4 separate operating systems. One for the desktop, one for mobile phones and one for tablets. That is not happening. Notice this comment:

> The tablet interface is presented by exactly the same OS and code that provides the phone, PC and TV interfaces, enabling true device convergence. Ubuntu is uniquely designed to scale smoothly across all form factors.

It is from here:

[http://www.canonical.com/content/ubuntu-unveils-tablet-experience-multi-tasking]("http://www.canonical.com/content/ubuntu-unveils-tablet-experience-multi-tasking")

Regards.

---

### Post by swanlee on 2013-02-22
> **grahammechanical said:**
> I am not meaning to be funny but Ubuntu is already available for Intel x86 CPUs. It is Ubuntu desktop AMD64 or i386.

As I understand Canonical's convergence strategy many of the features of Ubuntu Touch will be available in the images for Ubuntu desktop. We should not think of Canonical developing 3 or 4 separate operating systems. One for the desktop, one for mobile phones and one for tablets. That is not happening. Notice this comment:



It is from here:

[http://www.canonical.com/content/ubuntu-unveils-tablet-experience-multi-tasking](http://www.canonical.com/content/ubuntu-unveils-tablet-experience-multi-tasking)

Regards.


Still really does not answer my question,

I want to put Ubuntu touch on my X86 Tablet, I know Ubuntu desktop works on X86 as I have used it quite a bit on various netbooks but Ubuntu Touch OS is kind of confusing is it a new OS or just a touch skin on the current kernal? Why is it currently only limited to arm Android devices?

---

### Post by Nr90 on 2013-02-22
If you go to: [http://www.ubuntu.com/devices/tablet/partner](http://www.ubuntu.com/devices/tablet/partner)
You can see the high end requirements for new devices. As you can see it lists Intel 86 as an option.
So it will be possible for manufacturers to create X86 ubuntu tablets.
That said, I don't know if you'll be able to port it to your old windows tablet. It may lack useable drivers etc.

---

### Post by grahammechanical on 2013-02-22
>  Ubuntu Touch OS is kind of confusing is it a new OS or just a touch skin on the current kernal? Why is it currently only limited to arm Android devices?

Not a new OS. Ubuntu is a distribution not an OS anyway.

> The tablet interface is presented by exactly the same OS and code that provides the phone, PC and TV interfaces, enabling true device convergence. Ubuntu is uniquely designed to scale smoothly across all form factors.

> Even without chipset-specific optimisation, Ubuntu performs beautifully on entry level hardware. "Our four-year engagement with ARM has shaped Ubuntu for mobile" said Rick Spencer, VP Ubuntu Engineering at Canonical.

[http://www.canonical.com/content/ubuntu-unveils-tablet-experience-multi-tasking]("http://www.canonical.com/content/ubuntu-unveils-tablet-experience-multi-tasking")

Canonical does not need to invent hardware. This is hardware that is already in existence. It is also making use of Android technology and which devices is Android running on? Arm processors.

> The code release is a milestone in the development program for Ubuntu'€™s phone experience, and enables developers to port the platform to other devices. "€œOur platform supports a wide range of screen sizes and resolutions. Developers who have experience bringing up phone environments will find it relatively easy to port Ubuntu to current handsets"€ said Pat McGowan, who leads the integration effort that produced the images being released. €"We look forward to adding support for additional devices for everyday testing and experimentation."

[http://www.canonical.com/content/touch-developer-preview-ubuntu-be-published-21-february-2013]("http://www.canonical.com/content/touch-developer-preview-ubuntu-be-published-21-february-2013")

Canonical cannot do it all. Ubuntu is open source. So, there is an invitatiojn for others to port the code to other devices.

Regards.

---

### Post by swanlee on 2013-02-22
Ok still no real answer but from the vagueness I'm guessing that means no. I'm not a manufacturer or even a coder.
 
All I want to do is download Ubuntu touch to a USB stick and install it on my random no named older Win7 tablet. Just like I was able to do with Ubuntu desktop and various laptops/netbooks.
 
Will this be possible? Yes or No?

---

### Post by CDR Services on 2013-02-23
From what I read there will be two flavors the regular and the pro version, the pro version will be installed on quad core tablets and by adding a keyboard and mouse will switch to the desktop os!   Now I had occasion to try Ubuntu 12.04 on an HP all in one touch desktop pc. I ran it from the usb key and it took a little tinkering to get the display setup but the touch screen and onscreen keyboard worked out of the box!

---

### Post by 3rdalbum on 2013-02-23
> **swanlee said:**
> Ok still no real answer but from the vagueness I'm guessing that means no. I'm not a manufacturer or even a coder.
 
All I want to do is download Ubuntu touch to a USB stick and install it on my random no named older Win7 tablet. Just like I was able to do with Ubuntu desktop and various laptops/netbooks.
 
Will this be possible? Yes or No?

Currently: No. The Ubuntu tablet images only work on Nexus 7 and Nexus 10 tablets. They certainly don't work on any computer with an x86 CPU.

Near future: It may be possible to take the Ubuntu tablet interface and compile it for x86. One could roll an ISO image consisting of x86 Ubuntu with the tablet interface as a different session. It might not be much work to port the code to run on x86, maybe no work at all.

13.10: The tablet interface is expected to be installable from the repositories at this time.

---

### Post by Tomrade on 2013-03-09
Ubuntu touch images are currently based on android (cm mod) with ubuntu userland on top . so x86 images would need to ported to android-x86 until packages for "real ubuntu" are made

---

### Post by grahammechanical on 2013-03-11
> [COLOR=#000000]still no real answer[/COLOR]

That is because I do not know. And why should I know anything? I am not employed by Canonical. Even those who do know do not reveal things until they are officially supposed to reveal them. All I can do is quote from official sources. Such as this.

[http://www.jonobacon.org/2013/02/27/xda-developers-and-ubuntu-touch/](http://www.jonobacon.org/2013/02/27/xda-developers-and-ubuntu-touch/)

I do not expect Canonical to provide a multitude of Ubuntu images to work on a multitude of devices. They have not said that they will do that. In fact there is a big discussion going on in Canonical right now on how to better use their resources. And that will mean fewer ISO images. The Alternate ISO images were dropped from the 12.10 release. And we may find that in future there will be no interim releases only the LTS releases every two years and a development release that will be under continual development. The argument driving the adoption of this suggestion is the need to concentrate on the convergence strategy. It is seen as high risk with high rewards. And they have a limited time to bring it all together.

---

