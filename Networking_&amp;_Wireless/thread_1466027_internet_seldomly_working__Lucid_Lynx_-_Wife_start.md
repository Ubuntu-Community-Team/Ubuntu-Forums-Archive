---
title: "internet seldomly working  Lucid Lynx - Wife starts liking windows 7.  get me out !"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by ndefontenay on 2010-04-29
Hi.

I've installed lucid lynx only to find out the internet is not working properly. It's acting like I have a very slow connection and I get a lot of time outs. I have to refresh a whole lot of time in order to finally view a page.

Skype works fine though.

I don't understand what's going on.

During this time, windows 7 use the most of my 5MB bandwidth. I have to use it more now, help me out of this nightmare! My wife starts liking windows 7!

---

### Post by Lithaerien on 2010-04-29
Same here, except my Wifi won't connect at all. :/ I'm going back to 9.10 for now and hope that the rt2870 drivers work later on in lynx.

I tend to pull my hair out when it comes to wireless n support.

---

### Post by LieToPurify3 on 2010-04-30
I did a clean install of 10.04 and my wifi is extremely slow

---

### Post by jasonpeel on 2010-04-30
had same issue but found it to be firefox rather than the system or net. chrome works as fast as expected form my connection.

---

### Post by LieToPurify3 on 2010-04-30
I tried downloading chrome, but everything is just as slow.

---

### Post by xx58 on 2010-04-30
:rolleyes:Wait little and there be upgrade and it fixes Wifi problems. Best if you wait round one month, then everything will be just OK. Don't hurry.

---

### Post by ndefontenay on 2010-05-08
Still kind of slow :( It works ok with a normal bandwidth but rapidly degrade at peak time. Although it should work just fine however slowly.

---

### Post by pp7 on 2010-05-08
Are you talking about your wife or wifi?

---

### Post by Skaperen on 2010-05-08
> **ndefontenay said:**
> Still kind of slow :( It works ok with a normal bandwidth but rapidly degrade at peak time. Although it should work just fine however slowly.
Try setting a smaller MTU and see if that changes the performance behavior.  Open a shell terminal and do the following:```
sudo ifconfig wlan0 mtu 1024
```That assumes your wireless is "wlan0" (do just "ifconfig" alone to see the state of active network interfaces).  If this does improve performance, try values between that and 1500 in a binary search pattern to find the largest that works best for you.  I found that 1488 works for me and above that things get very slow.

Note: doing the above will NOT be persistent across a reboot.  If it does work for you, let us know what value does work well consistently, and someone can tell you how to make it be persistent so you don't have to do that each time.

If this does not work, we've ruled out one possible cause.

---

