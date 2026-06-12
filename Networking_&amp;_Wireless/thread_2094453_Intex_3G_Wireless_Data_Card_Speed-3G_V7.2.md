---
title: "Intex 3G Wireless Data Card Speed-3G V7.2"
date: 2012-12-13
forum: Networking &amp; Wireless
---

### Post by yajnamurti on 2012-12-13
I have a Intex 3G Wireless Data Card Speed-3G V7.2 and it comes with a .deb file to install it in Linux. I did it and after that my Ubuntu 12.04 became a little messy with some pop up messages asking my password a lot of times. Now I got a new laptop and before installing the .deb file for Intex 3G Wireless Data Card Speed-3G V7.2 I would like that some expert look at it and edit it, if necessary. The .deb file is at this address:

[https://docs.google.com/open?id=0B-nrS5WTQ60oRTVfVzFYdkdXdE0](https://docs.google.com/open?id=0B-nrS5WTQ60oRTVfVzFYdkdXdE0)

Thank in advance for any help.

---

### Post by N3XU5 on 2012-12-13
Did you search the internet for other drivers?

---

### Post by yajnamurti on 2012-12-13
> **N3XU5 said:**
> Did you search the internet for other drivers?

I tried but did not find anything so far.

---

### Post by yajnamurti on 2012-12-17
Anybody there to help me? :confused:

---

### Post by mlentink on 2012-12-17
I think you will not get many people to download an executable (which a .deb basically is) from an untrusted site. What site did you get that installer from in the first place?

This is a site I found, perhaps you can find help there?  [http://intexuae.com/?page_id=267](http://intexuae.com/?page_id=267)

---

### Post by squakie on 2012-12-17
Did these messages say something like enter keyring password, or perhaps asking for a network passphrase/passkey?

Do you have an example with the exact text so we can see?

---

### Post by chadk5utc on 2012-12-17
what I suggest is try to install this within a terminal and post the output here as it will be more helpful with troubleshooting. Also there should be a config file after install which can be useful.
I believe this should get you going
> dpkg -i yourfile.deb
Also worth mention if it came with a linux driver there should be manufacturer support

---

### Post by GordThompson on 2012-12-17
> **yajnamurti said:**
> I have a Intex 3G Wireless Data Card Speed-3G V7.2 and it comes with a .deb file to install it in Linux. I did it and after that my Ubuntu 12.04 became a little messy with some pop up messages asking my password a lot of times.
Are you saying that 

1. the password prompts appeared *during *the install, or 

2. that they kept appearing *after *the install? 

#1 would not be too surprising (although I would really only expect to be prompted once)

#2 would be bad

---

### Post by GordThompson on 2012-12-17
> **mlentink said:**
> I think you will not get many people to download an executable (which a .deb basically is) from an untrusted site.[]("http://intexuae.com/?page_id=267")
I did. Unpacked it using Archive Manager and had a look around. Looks pretty standard to me.

---

### Post by yajnamurti on 2012-12-17
First of all THANK YOU very much for your reply. I did install it and I tried it and amazingly it is working fine. Maybe I had a problem in my older laptop. For while I will mark as solved this thread, if I find any problem later I will come back. 

Thank You!   ):P

---

