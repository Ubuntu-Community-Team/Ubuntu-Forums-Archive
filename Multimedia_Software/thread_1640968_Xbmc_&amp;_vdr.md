---
title: "Xbmc &amp; vdr"
date: 2010-12-08
forum: Multimedia Software
---

### Post by markfaine on 2010-12-08
In researching a tv tuner plugin for XBMC I came across vdr and vdr-plugin-streamdev and [this page]("http://bit.ly/eOS3Wr") that shows how to integrate the two.  However, it seems sort of dated and I can't find anything newer.  I'm looking for a PPA for vdr and vdr-plugin-streamdev that will work work with Maverick and XBMC Dharma. 

Know anything?

---

### Post by caribo on 2010-12-29
I use maverick + VDR 1.7.16 + XBMC Dharma PVR testing

I use the lucid packages from yaVDR via their ppa ppa:yavdr/testing-vdr along with opdenkamp's XBMC build at ppa:lars-opdenkamp/xbmc-master-pvr

note that if you use add-apt-repository for the VDR packages you will need to amend the corresponding file in /etc/apt/sources.list.d to state lucid, rather than maverick.

I would prefer a reliable maverick build for VDR, but the above works OK..

---

### Post by Asterix99 on 2011-01-05
Hi,  how did you install VDR 1.7.16 on maverick? It is not in the official repository :-(

---

### Post by kakaouskia on 2011-01-18
Hi caribo,

I have added the yavdr repositories as you did, and installed xbmc dharma PVR using:

sudo add-apt-repository ppa:lars-opdenkamp/xbmc-pvr
sudo apt-get update
sudo apt-get install xbmc libva1

When I go to Live TV section, I get error: No PVR clients available, please check your settings or backend

Any ideas as why this is happening? I must be missing configuration somewhere

Also, where does channels.conf go in yaVDR 1.7.16? 

Thanks in advance!

---

### Post by chessplayer on 2011-01-18
Hi,

channels.conf goes to /var/lib/vdr as far as I remember (there should be some samples in there as well).

Cheers,

chessplayer

---

### Post by chessplayer on 2011-01-18
Hi,

channels.conf goes to /var/lib/vdr as far as I remember (there should be some samples in there as well).

Cheers,

chessplayer

---

### Post by kakaouskia on 2011-01-19
Hi,

thanks for the reply. I will try to put the file there and see how it goes.

---

### Post by deadite66 on 2011-01-31
i've been trying to get this working too but not much luck.

i did work out you need scan with '-o vdr' option to get it in the right format.

i just can't get xbmc-pvr to see vdr, just get no clients available.

---

### Post by kakaouskia on 2011-01-31
Hello again.

@chessplayer: you were rght about the locatio n of the channels.conf. Thanks!

@deadite66: You can try this:
- Open XBMC
- Go to System -> Addons -> Installed Addons -> PVR Clients
- Enable the client you want to use from the list of available clients
- Configure the client (refer to the appropriate client's documentation for details)
- Enable Live TV

I have tried this approach with TvHeadend HTSP client; I assume the VDR configuration can be similar to this.

Hope this helps!

Cheers,
Kakaouskia

---

