---
title: "Tether iPhone 5 via USB"
date: 2012-12-21
forum: Networking &amp; Wireless
---

### Post by Newbunto on 2012-12-21
I am trying to tether an iPhone 5 via USB with Ubuntu 12.04.1 LTS. The kernel version is 3.2.0-35.

I have installed
    ipheth-utils
    libimobiledevice-dev
    libimobiledevice-utils

When I plug the iPhone in I get dialog boxes about "a medium with digital photos" and "a digital audio player" which I Cancel but I don't see anything about networking.

What, if anything, should I do with those dialog boxes?

Should I expect to see something about networking?

Is there any way to tell whether tethering is working at all?

Is it expected that this will work at all?

(I have enabled Personal Hotspot on the iPhone - enabled for WiFi and USB, not Bluetooth - and am only trying to get it working via USB. For simplicity I have turned off WiFi on the Ubuntu PC.)

---

### Post by haqking on 2012-12-21
> **Newbunto said:**
> I am trying to tether an iPhone 5 via USB with Ubuntu 12.04.1 LTS. The kernel version is 3.2.0-35.

I have installed
    ipheth-utils
    libimobiledevice-dev
    libimobiledevice-utils

When I plug the iPhone in I get dialog boxes about "a medium with digital photos" and "a digital audio player" which I Cancel but I don't see anything about networking.

What, if anything, should I do with those dialog boxes?

Should I expect to see something about networking?

Is there any way to tell whether tethering is working at all?

Is it expected that this will work at all?

(I have enabled Personal Hotspot on the iPhone - enabled for WiFi and USB, not Bluetooth - and am only trying to get it working via USB. For simplicity I have turned off WiFi on the Ubuntu PC.)

I dont use Ubuntu or an iPhone.  However i did set up my brothers laptop the other night Running 12.04 and iPhone 5.  I turned on tethering on the iPhone then plugged it in and worked straight away.

I didnt need to add anything, took me 30 seconds of guessing what to do.

---

### Post by Whoopie on 2012-12-21
Support for the iPhone 5 was included in kernel 3.7. You could open a bug report to ask if the commit was backported to kernel 3.2.

The commit is [https://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=commitdiff;h=af1b85e49089f945deb46258b0fc4bc9910afb22](https://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=commitdiff;h=af1b85e49089f945deb46258b0fc4bc9910afb22)

---

### Post by Newbunto on 2012-12-24
I should add that this same Ubuntu PC works correctly with an iPhone 4.

Edit: "works" means that I get a new "ethernet" interface, eth1, and it gets an IP address and, by unplugging the real wired ethernet, I can even see that the tethering works. So, definitely seems to be that an iPhone 5 is not recognised. Given that 3.7 must be a long time away, I will be hoping for a backport.

---

### Post by haqking on 2012-12-24
> **Newbunto said:**
> I should add that this same Ubuntu PC works correctly with an iPhone 4.

Edit: "works" means that I get a new "ethernet" interface, eth1, and it gets an IP address and, by unplugging the real wired ethernet, I can even see that the tethering works. So, definitely seems to be that an iPhone 5 is not recognised. Given that 3.7 must be a long time away, I will be hoping for a backport.

3.7 was release on 11 december.

Perhaps my brothers phone was a iPhone 4 then but I am pretty certain it was a 5, this was like first week fo December and he had just got it.

Oh well

---

### Post by Newbunto on 2012-12-25
> **haqking said:**
> 3.7 was release on 11 december.

Yes. I meant "a long time away" until it comes through to me.

I've let it update the kernel whenever it has asked. Do I need to do something different in order to upgrade to a later version of Ubuntu? (Sorry for the newb question.) Even then, if [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions) is accurate, I don't think I could get to kernel version 3.7 right now.

---

### Post by Newbunto on 2012-12-31
> **Whoopie said:**
> You could open a bug report to ask if the commit was backported to kernel 3.2.

Done. (I think!)

---

### Post by Whoopie on 2013-01-04
Support was added to kernel 3.2.36. -> [https://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=commitdiff;h=2e1ab4c280688604c7f3db6c75c1ef6ffeac60b2](https://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=commitdiff;h=2e1ab4c280688604c7f3db6c75c1ef6ffeac60b2)

BTW, you could use this [howto]("http://www.downtowndougbrown.com/2012/12/tethering-iphone-5-over-usb-on-ubuntu-12-10-ugly-hack/") for an interim solution.

---

### Post by Newbunto on 2013-01-18
> **Whoopie said:**
> Support was added to kernel 3.2.36.

How can you tell what kernel that change went in?

My computer upgraded itself today to "3.2.0-36-generic" and plugging in the iPhone  5 doesn't seem to have the desired effect.

---

### Post by Whoopie on 2013-01-18
Well, kernel 3.2.36 is NOT the ubuntu package linux-image-3.2.0-36-generic.

Just wait for the next linux-image update. The master-next git tree already has kernel 3.2.37 merged. -> [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=shortlog;h=refs/heads/master-next](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-precise.git;a=shortlog;h=refs/heads/master-next)

---

### Post by Newbunto on 2013-01-31
My computer upgraded itself today to "3.2.0-37-generic" and plugging in the iPhone  5 doesn't seem to have the desired effect.

---

### Post by xe1ufo on 2013-01-31
Question: (Mine is the Iphone IV, IOS-6) On the Iphone itself, did you actually go into: Settings>>General>>Cellular then scroll down to Personal Hotspot and turn it on? Just curious.

---

### Post by Newbunto on 2013-02-21
My computer upgraded itself today to "3.2.0-38-generic" and plugging in the iPhone  5 seems to have the desired effect. **Awesome!**

In fact this post is being done using the iPhone 5 as the network interface.

I note that [FONT=Courier New]lsusb[/FONT] still doesn't recognise the iPhone 5. This is presumably only cosmetic. It does mean though that I can't be sure which exact kernel update added the necessary support since I was using [FONT=Courier New]lsusb[/FONT] to check each update after I reported the original issue.

---

