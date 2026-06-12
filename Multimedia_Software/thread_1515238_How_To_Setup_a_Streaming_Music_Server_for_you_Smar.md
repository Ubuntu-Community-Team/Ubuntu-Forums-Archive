---
title: "How To: Setup a Streaming Music Server for you Smart Phone"
date: 2010-06-22
forum: Multimedia Software
---

### Post by slooksterpsv on 2010-06-22
All,

I had trouble finding this on the internet, so I'm going to share with you how I setup an MP3 Streaming server so that I could stream music to my Blackberry Curve 8330. Let's get started:

1. Install the following packages:
```

sudo apt-get install apache2 php5 php5-common php5-cli php-mysql mysql-server phpmyadmin

```

2. Download, extract, and install GNUMP3D:
```

wget http://savannah.gnu.org/download/gnump3d/gnump3d-3.0.tar.gz
tar -xvf gnump3d-3.0.tar.gz
cd gnump3d-3.0
sudo make install

```

3. Configure Gnump3d:
```

sudo gedit /etc/gnump3d/gnump3d.conf

```
Go to line 109 and change to:
```

root = /path/to/music #mine was /home/<username>/Music

```
Go to line 336 and change to:
```

always_stream = 0

```
This will allow it to download to your MP3 device instead of trying to open it through an m3u file (which blackberry does not support).
Save and exit.

4. Start Gnump3d and have it index
```

sudo gnump3d &

```

After a few moments, navigate to:
[http://127.0.0.1:8888](http://127.0.0.1:8888)
and you should be able to see your music on the computer. What about on your phone or other mobile device? - Well you would need to setup your modem in bridge mode, ip passthrough mode, or do a translation from the public IP to a private IP (what is the term my minds went blank). Once you've done that, on your blackberry for example, you'd just navigate to:
xx.xx.xx.xx:8888 - where xx.xx.xx.xx is the public IP address of your computer. Google search your brand of modem or that to find out how to do all this.

Now for SmartPhones, the theme may seem out of whack, but you can still search and click on songs to play.

This works wonders and is a great way to stream your music I've tried: netjukebox squeezebox, etc. and nothing comes close to gnump3d as far as simplicity, and usability.

If you need further information or help let me know.

Thanks!

---

### Post by Jamesmerr on 2010-07-23
Hello - I followed your instructions verbatim and everything completed with no issues.  When I try to navigate to localhost:8888 from the machine gnump3d was installed on i get a completely blank page.  I can navigate to all other pages localhost:8888/copying, browse, custom playlist, search, etc.  Basically every page works except for the root domain "localhost:8888"

Any thoughts?

---

### Post by slooksterpsv on 2010-07-23
> **Jamesmerr said:**
> Hello - I followed your instructions verbatim and everything completed with no issues.  When I try to navigate to localhost:8888 from the machine gnump3d was installed on i get a completely blank page.  I can navigate to all other pages localhost:8888/copying, browse, custom playlist, search, etc.  Basically every page works except for the root domain "localhost:8888"

Any thoughts?

Try going through it like this instead:
[http://127.0.0.1:8888](http://127.0.0.1:8888)

Localhost I've had problems with in the past not executing php code.

---

### Post by Jamesmerr on 2010-07-25
> **slooksterpsv said:**
> Try going through it like this instead:
[http://127.0.0.1:8888](http://127.0.0.1:8888)

Localhost I've had problems with in the past not executing php code.

hmm, yields same issue as before, blank page

---

### Post by ihavoc on 2010-08-16
I was getting the blank page as well and this worked for me.

```
sudo gedit /etc/gnump3d/gnump3d.conf
```

change 
```
user = nobody
```
to
```
user = root
```

then I was able to see everything.

Thanks to slooksterpsv, for posting this.

---

