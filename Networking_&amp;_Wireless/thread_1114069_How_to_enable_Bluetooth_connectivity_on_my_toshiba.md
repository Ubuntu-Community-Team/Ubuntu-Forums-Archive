---
title: "How to enable Bluetooth connectivity on my toshiba a100 laptop"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by scrypt on 2009-04-02
I am trying to connect my toshiba satelite a100 laptop to my mobile phone via Bluetooth connectivity.

But I cannot seem to establish a connection.

How can I go about this??

---

### Post by scrypt on 2009-04-02
I have trawlled google and a couple of forums, but i have not found much.

I did find this though:

So, apparently Ubuntu is not turning on the bluetooth radio. I read in one of the threads here that some people can turn on bluetooth on Toshibas with
Code:

$toshset -bluetooth on

Unfortunately, when I try that I get:
Code:

$sudo toshset -bluetooth on

required kernel toshiba support not enabled

Does anybody know what this means?

---

### Post by scrypt on 2009-04-03
Im still strugling with this.

Can anyone help

---

### Post by rajamouli2000 on 2009-04-29
You need to install omnibook driver.
 
There is a very nice howto in our forum [here]("http://ubuntuforums.org/showthread.php?t=316358&highlight=omnibook")

In the post, Azriphale neatly explains building, installing and loading omnibook. He also explains how to keep enable and disable bluetooth from command line. 

I tried this for my Toshiba Satellite M300, it works seamlessly.

---

### Post by Albert Que on 2009-05-09
I own a toshiba satellite A200 (phoenix BIOS) running ubuntu 9.04 (Jaunty Jackalope) and had the same problem. 
That worked to me:
[https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374](https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374)

(search "Tim Richardson  wrote on 2008-07-08")

---

