---
title: "mythbuntu faq"
date: 2014-12-04
forum: Mythbuntu
---

### Post by Kevin McCready on 2014-12-04
So I followed links and ended up at mythbuntu.org

Either way, here or at Mythbuntu.org I still don't know:
1. What's MythTV
2. What's PVR
3. Can I run my ordinary linux WITH mythtv?

Yes I can google to find out, but jeez.

---

### Post by Kevin McCready on 2014-12-04
The about page  = [http://www.mythbuntu.org/home](http://www.mythbuntu.org/home)
didn't cast light on these questions either.

---

### Post by wyliecoyoteuk on 2014-12-04
> **Kevin McCready said:**
> So I followed links and ended up at mythbuntu.org

Either way, here or at Mythbuntu.org I still don't know:
1. What's MythTV
2. What's PVR
3. Can I run my ordinary linux WITH mythtv?

Yes I can google to find out, but jeez.

1. The mythical Convergence device- a multimedia entertainment centre
2. PVR personal Video Recorder (also known as DVR, Digital Video Recorder) needs a tv tuner. (This is explained on the Mythbuntu home page, I guess you didn't read the first paragraph).
3. Yes, you can install it in Ubuntu, it is in the repos as MythTV. frontend (client) and backend (server).

Mythbuntu is a pre-built dedicated distro for MythTV, based on Ubuntu, and you can install regular Ubuntu stuff on it as well, including the Unity desktop.

I run a backend on a small minitx box with a dual tv tuner to store my TV recordings, video , pictures and music. I run frontends on the other Linux and Android devices on my home network to watch play the media, but you can run a front and backend on the same PC

---

### Post by tgm4883 on 2014-12-04
> **Kevin McCready said:**
> So I followed links and ended up at mythbuntu.org

Either way, here or at Mythbuntu.org I still don't know:
1. What's MythTV


It's a DVR

> **Kevin McCready said:**
> 
2. What's PVR


I've changed it to the more common "DVR"


> **Kevin McCready said:**
> 
3. Can I run my ordinary linux WITH mythtv?

Yes I can google to find out, but jeez.

MythTV is just a software application, so yes you can.

---

### Post by wyliecoyoteuk on 2014-12-06
Actually, it is a lot more than a DVR.

But then all of the OP's questions are actually answered on the Mythbuntu home page, so maybe he didn't actually read it.

> Mythbuntu is an official Ubuntu flavor focused upon setting up a standalone MythTV based Digital Video Recorder (DVR) system. 

> Mythbuntu uses the XFCE desktop. All unnecessary standard Ubuntu applications such as LibreOffice, Evolution, and a full Gnome desktop are not installed in a default Mythbuntu install. If at any time a user wants to, they can install ubuntu-desktop, kubuntu-desktop, or xubuntu-desktop and add a full desktop onto their installation.

> This architecture allows simple conversions from a standard desktop to a Mythbuntu machine and vice versa.

I know people are lazy, but jeez....no neded to even Google it.

---

### Post by Kevin McCready on 2014-12-07
So now I know it's a piece of software available via my repos. Thanks for that.

I'm assuming I can somehow plug my computer with mythtv software into the TV and record stuff and play it back later.

Can I suggest you don't assume any prior knowledge? ie PVR/DVR and other acronyms should be spelt out when first used in an article.

I still have no idea what backend frontend means, but I guess I can google that too.

Anyway, thanks for your time.

---

### Post by Bucky Ball on 2014-12-07
> **Kevin McCready said:**
> I'm assuming I can somehow plug my computer with mythtv software into the TV and record stuff and play it back later.



Don't think so. As was stated, you need a TV tuner to do that, and I presume this means an internal TV card capable of this or a USB dongle (which is what I have and it works fine). You plug the TV antennae into the TV card or USB and there you go. I don't go as far as MythTV as don't need all the bells and whistles and don't record stuff. I use MeTV which is also in the repos, and I can record with it if I want, but never have.

You need someway of getting the antennae into the computer. Generally, a splitter is used with one antennae cable to the TV and one to the computer. Never the twain shall meet, though. They are both completely independent. You would then watch what you've recorded on the computer via a HDMI or VGA cable to the TV.

Anyone feel free to correct me if I'm wrong. I personally use an Odroid as a media server to pick up anything on the household computers I want to watch on the TV. It connects to the TV via HDMI and I use XBMC.

---

### Post by kpatz on 2014-12-08
MythTV is flexible and can be set up in a number of ways.

The basic architecture is there is a backend (server) and a frontend (client), both of which can run on a single machine, or they can be run on separate machines.  Depending on your needs, you may even have more than one frontend or backend.

The backend takes care of recording, scheduling, and storage.  This is where the TV tuner card(s) or dongle(s) are installed.  The frontend acts as the client, providing the user interface and playback on whatever display you're using (computer monitor, TV, etc).  If you have multiple TVs in the house, you may decide to have a single backend and separate frontends for each TV, then each TV can watch a different recorded show at the same time, or even different live shows if you have enough tuner(s).  The backend could be one of the machines also acting as a frontend, or it could be a separate machine on the network.  For example, you could have a powerful server in your office with plenty of storage as your backend, and small fanless HTPC machines near each TV as the frontends.

Mythbuntu is a distribution that includes an XFCE version of Ubuntu (similar to Xubuntu) and MythTV already included.  This makes it easier to set up frontends especially.  You don't have to use Mythbuntu though.  You can take a machine that already has any of the *buntus installed and install the MythTV packages.  For example, if you have a server already you want to use as a backend, you can just install the backend packages there, and then install the frontend packages (or Mythbuntu) on the frontends.

So, for backends you'll want tuner card(s)/dongle(s) and plenty of storage.  For frontends, you'll want something with decent video performance, HDMI output and not too bulky or noisy if it's going to be in your living room (depending on your needs).  nVidia chipsets tend to be better supported in Linux than ATI/AMD, though either will work.  I run a dedicated MythTV box in my home theater cabinet (frontend and backend both on the same box).

---

### Post by tgm4883 on 2014-12-08
> **wyliecoyoteuk said:**
> Actually, it is a lot more than a DVR.

But then all of the OP's questions are actually answered on the Mythbuntu home page, so maybe he didn't actually read it.







I know people are lazy, but jeez....no neded to even Google it.

To be fair, I did change the first two things you quoted on the Mythbuntu website after I read the OP's post.

---

### Post by wyliecoyoteuk on 2014-12-08
> **tgm4883 said:**
> To be fair, I did change the first two things you quoted on the Mythbuntu website after I read the OP's post.


OOPs! In that case , I wholeheartedly apologise!

I would add that MythTV can run a frontend and a backend on the same device.
Frontends can be run on any platform, Windows, Mac, Linux or Android.
The backend manages the hardware tuner, recording and storage, the frontend is the player and control interface.
MythTV can also act as a DNLA server, it apparently supports Airplay as well.

I use XBMC as a frontend on Android devices, I can watch recordings or liveTV, play music, view pictures etc. on my Tablet or my AndroidTV box, or any other device on my network.

---

### Post by Bucky Ball on 2014-12-09
> **wyliecoyoteuk said:**
> 

I use XBMC as a frontend on Android devices, I can watch recordings or liveTV, play music, view pictures etc. on my Tablet or my AndroidTV box, or any other device on my network.

+1. I hark back to my Odroid. xbmc works better on that than Lubuntu for TV stuff. ;)

---

