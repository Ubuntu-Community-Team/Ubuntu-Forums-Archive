---
title: "problem with automatically loading kernel module for wireless usb adapter"
date: 2012-03-24
forum: Networking &amp; Wireless
---

### Post by Unkraut on 2012-03-24
Hello!

My sister's computer is running Ubuntu 10.04. Recently we bought a cheap wireless USB adapter. Turned out I had to compile drivers from source (don't know anymore where from ATM, but the driver source I downloaded is in a folder called RTL8188C_8192C_8192D_USB_linux_v3.3.2_3192.20120103 if that's interesting to anyone).
That went without problem, I created the directory /lib/modules/$(uname -r)/8192cu and stored the compiled file 8192cu.ko therein, then I added the line "8192cu" to /etc/modules. After reboot everything seemed to work, the module was loaded automatically.
But now after a kernel update it didn't work anymore. So of course I did the same thing again, compiled the kernel module again, created the directory /lib/modules/$(uname -r)/8192cu (with the updated kernel version) and stored the newly compiled 8192cu.ko therein.
But this time after reboot it doesn't work. The module is not loaded automatically. If I do "insmod /lib/modules/$(uname -r)/8192cu/8192cu.ko" though the driver is loaded and works fine.
What have I done wrong? And also, of course what I do seems to be quite cumbersome, and actually I have no really deep knowledge of what I'm doing theoretically here. Also I would like to keep things simple for my sister. What should I do?

Kind regards

Unkraut

---

### Post by chili555 on 2012-03-24
Ahhhh! The beauty of compiled from source driver modules! They are specific to your kernel version and your gcc and g++ versions among other things. Therefor, when a new kernel version, also known as linux-image is installed, the compiled from source driver modules must be compiled again for the new kernel. That's the way it works. There is no slick, easy work-around.

Eventually, the driver is included in the mainstream kernel:> /lib/modules/[COLOR="Red"]3.0.0-16-generic[/COLOR]/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/[COLOR="Red"]rtl8192cu[/COLOR].koSo, for those who are running newer versions of Ubuntu, it's included out of the box! You could certainly upgrade your sister to 11.10.

Here is what I suggest you do:```
cd Desktop/RTL8192  <---or wherever you extracted the files
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
exit
```Now does it work as expected?

---

### Post by Unkraut on 2012-03-24
Thanks. But that's (almost) exactly what I did. Sorry if I wasn't clear enough. I recompiled the driver after the kernel upgrade, and it works if I do "insmod /path/to/8192cu.ko" by hand. But it is not loaded automatically anymore at startup.
To be more precise: The newly compiled kernel module resides in "/lib/modules/$(uname -r)/8192cu/8192cu.ko" (uname -r == really up-to-date kernel version, no mistake here). I added the line "8192cu" to /etc/modules. But still it is not loaded on startup. It worked with the previous kernel version where the file was "/lib/modules/<previous kernel version>/8192cu/8192cu.ko".
So the problem is that the driver is not loaded automatically. Any idea what's wrong here?

However, your suggestion to install 11.10 will certainly be the most comfortable way in the long run. I just was not sure if the driver would be included there or if I'd still have to compile. Thanks for removing that doubt. ;)

Edit: Sorry I didn't pay much attention to this part of your answer:
> Here is what I suggest you do:```
cd Desktop/RTL8192  <---or wherever you extracted the files
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
exit
```Now does it work as expected?
I had not done "make install" before, instead just copied the .ko file in the above-mentioned cumbersome way.
Now after following your advice everything works as expected. Thank you very much!

---

### Post by chili555 on 2012-03-24
> Thanks. But that's (almost) exactly what I did. Can you try it again and copy and paste the last five lines of 'make install' here so we can examine it? It will also be interesting to see:```
dmesg | grep 8192
cat /etc/modules
```Thanks.

---

### Post by Unkraut on 2012-03-25
Ah, it seems we were posting at the same time.
See my last reply (edited). I had not done "make install" at first. But then I did and now everything is fine.
Thank you very much for your help!

---

### Post by Unkraut on 2012-03-26
Okay, so installed Ubuntu 11.10. Turns out the driver that comes with it has the same problems as before. So I still have to use the proprietary driver and compile it on my own.
No big problem, but... is there a way to recompile and reinstall the driver automatically whenever a new kernel update comes? I've written a small bash script that just goes to the directory where the driver source is stored and then does
```

make clean
make
make install

```
Is there a way to run this script automatically after a new kernel version is installed?
My idea is to simply put it into /etc/init.d and set it up to be run at startup with an additional if-clause that checks if a kernel update has taken place since the last boot. I only don't know how to do the latter.
Someone have an idea? Any help appreciated.

Kind regards
Unkraut

---

### Post by chili555 on 2012-03-26
> Turns out the driver that comes with it has the same problems as before.Like what? Is it something that's easily correctible?

---

### Post by Unkraut on 2012-03-26
Okay, read this article: [https://help.ubuntu.com/community/DKMS](https://help.ubuntu.com/community/DKMS) and followed it. This seems to be the solution. Had to add another directive to the dkms.conf file as specified in the article, namely DEST_MODULE_LOCATION=...
Without really knowing what I should type in there I added
DEST_MODULE_LOCATION="/kernel/8192cu/"
Hope it will work. If not, I'll be back. :p

EDIT: Whoops, didn't see this new reply:
> **chili555 said:**
> Like what? Is it something that's easily correctible?

Sorry, I didn't write it in the OP. The wifi adapter was recognized but unable to connect. That had already been the problem with Ubuntu 10.04.
But I built the proprietary driver and now also (hopefully) successfully integrated it with DKMS so that I won't have to do it again by hand with every kernel update.

I'll mark this as solved. Thank you for your ready support, chili! :)

---

