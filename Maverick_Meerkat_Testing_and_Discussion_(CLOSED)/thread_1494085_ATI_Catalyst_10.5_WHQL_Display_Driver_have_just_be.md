---
title: "ATI Catalyst 10.5 WHQL Display Driver have just been released"
date: 2010-05-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-05-26
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)
 
What changes would it bring to the current fglrx driver?
 
Thanks in advance.
 
p.s when can we except the next iso release i am waiting for 10.04.1 version in order to reinstall ubuntu 
hopefully all/most the problems i had with 10.04 be fix in this version.

---

### Post by andrewthomas on 2010-05-26
> **aviramof said:**
> [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)
 
What changes would it bring to the current fglrx driver?
 Did you read the link?

 > **aviramof said:**
> 
p.s when can we except the next iso release i am waiting for 10.04.1 version in order to reinstall ubuntu 
hopefully all/most the problems i had with 10.04 be fix in this version.
You are joking, right?

---

### Post by aviramof on 2010-05-26
Forget it with this sort of replies i'd better get bie on my own.

---

### Post by crjackson on 2010-05-26
> **aviramof said:**
> [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)
 
What changes would it bring to the current fglrx driver?
 
Thanks in advance.
 
p.s when can we except the next iso release i am waiting for 10.04.1 version in order to reinstall ubuntu 
hopefully all/most the problems i had with 10.04 be fix in this version.

The driver SHOULD fix some bugs, have better graphics acceleration and support the OS a little better.

[B]The following section provides a brief description of resolved issues with the latest version of the ATI Catalyst&#8482; Linux software suite. 

These include:[/B]

* Changes to the color gamma value are now retained in Catalyst Control Center and reflected on the display after X-server restart
* System will now resume properly after hibernation/suspend mode
* Flickering corruption no longer observed while running OpenGL applications with CrossFire&#8482; enabled
* [RHEL4u8] DisplayPort display will now light up after being hotplugged
* [SUSE 11.1] Enabling more than 4 single independent desktops no longer causes black screen hang on starting X

Every release of Ubuntu features updated software applications, a newer kernel with improved hardware support.  It's really too far away to KNOW all the changes, but browse through the posts in this forum and you can pick up a lot of speculation on what's to be included.

Don't get too put off by some of the responses. Just let it go. Take a deep breath and hopefully someone will jump in and politely present the information you are requesting.

---

### Post by aviramof on 2010-05-27
Thanks for the info and i just want to know when can i except the next iso that as i been told should be released in june i 
hope this iso would have already include a working plymouth and a better grub 2 and etc.

---

### Post by ranch hand on 2010-05-27
According to this;

[https://wiki.ubuntu.com/MaverickReleaseSchedule](https://wiki.ubuntu.com/MaverickReleaseSchedule)

It is due out on 7-22.

I would not hold your breath about plymouth working.  If it does not work on your hardware by now it probably will get worse.

There is nothing that I can see that is a real problem in grub now.

---

### Post by aviramof on 2010-05-27
My problem with grub is that it doesn't always update the mbr on my main HD so after restart i have no grub menu and i am forced
to enter live cd again and install grub on sda and sdb manually and i really don't understand why it does this my setting is not uniq at all.
 
And as i see now it's on the July 29th not July 22nd so there is a long time till then so maybe i would wait till Maverick Release before i try ubuntu again
i hope this version at least would not dissapoint me in the end.

---

### Post by Starks on 2010-05-27
WHQL
Linux

Choose one.

---

### Post by airtonix on 2010-05-27
> **aviramof said:**
> Forget it with this sort of replies i'd better get bie on my own.

Well if you knew what WHQL means.

*[http://en.wikipedia.org/wiki/WHQL_Testing](http://en.wikipedia.org/wiki/WHQL_Testing)*
> **Windows Hardware Quality Labs** testing or WHQL Testing is Microsoft's testing process which involves running a series of tests on third-party (i.e. non-Microsoft) hardware or software, and then submitting the log files from these tests to Microsoft for review. The procedure may also include Microsoft running their own tests on a wide range of equipment, like different hardware and different Microsoft Windows editions.

Products that pass the WHQL tests get to use a **"Certified for Windows"** logotype, which certifies that the hardware or software has had some share of testing by Microsoft to ensure compatibility. The actual logo used depends on the version of Windows.


No doubt the sarcasm is due to this.

---

### Post by aviramof on 2010-05-27
This is just the name of the driver i thought you'd be smart enaf to ignore it and understand the relevent of it to the fgrlx driver.

---

### Post by ELD on 2010-05-27
No offense to [aviramof]("http://ubuntuforums.org/member.php?u=1009662") but [andrewthomas]("http://ubuntuforums.org/member.php?u=1011186") was right, everything you needed to know was on the link you posted yourself about the ATi driver. Release notes aren't made for fun buddy.

---

### Post by aviramof on 2010-06-04
I just need to know just two things is there already an fglrx driver for  [[COLOR=#000000]Maverick Meerkat [/COLOR]]("http://ubuntuforums.org/forumdisplay.php?f=385") because if it uses the same 1.75 as lucid i don't see a reason why it would't have it.
 
and does the compiz pacages from the lucid ppa would work?
 
[https://launchpad.net/~compiz/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~compiz/+archive/ppa?field.series_filter=lucid)
 
Thanks in advance.

---

