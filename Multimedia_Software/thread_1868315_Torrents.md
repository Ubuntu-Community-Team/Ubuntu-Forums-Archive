---
title: "Torrents"
date: 2011-10-24
forum: Multimedia Software
---

### Post by 3v3rgr33n on 2011-10-24
;)  I just have a question with regards to torrents...

can anyone please explain what a torrent is; a month ago while i was still using windows i discovered BitTorrent. i thought it was a simple process whereby you just download a torrent from the internet then BOOOM! you get whatever you wanted to download.

Unfortunately it didn't work...yesterday i saw Torrent Software on the software center. Can someone please clarify this torrent issue. What torrent client do you recommend? how do peers come in the picture with regards to torrents?

---

### Post by Rasa1111 on 2011-10-24
I like to use transmission (installed by default) or deluge.

I like transmissions for just downloading torrents, but deluge for creating/uploading them.

Years ago, when I first learned of torrents..
I thought the same as you..

"just download this file, and when its done, BAM, got what ya want!"..

It wasnt that easy... but once I figured it out.. it was still super easy.  lol

I won't go into exactly how it all works, mostly because i lack the proper terms to describe things..
But it works like this..

1) You download the torrent.
2) you open the torrent you downloaded in your torrent client (transmission/deluge/etc)
3) let the torrent download the material in the client.
4) when finished, open the folder and use whatever you downloaded.

Usually..
if you have a torrent client installed..

You can just download a torrent, and when its done, double click it (the torrent file/download), and it will open in your torrent client and download. 

Make sure you download torrents that have "seeders"..
or your downloads will never finish. lol

sorry i didnt go into it more, but hopefully that gets you started.
good luck, have fun. :)

---

### Post by 3v3rgr33n on 2011-10-25
dude! i'm using KTorrent. everything i download ; the status is always --"stalled"

---

### Post by satanselbow on 2011-10-25
> **3v3rgr33n said:**
> dude! i'm using KTorrent. everything i download ; the status is always --"stalled"

I don't use ktorrent BUT "stalled" usually means there is a problem with your internet connection - with regards to torrents. You may see an icon in the ktorrent status bar that says something along the lines of "DHT Unavailable" or "No direct connections".

Have a look at the "Listening port" in ktorrent options - probably set at 6881 or there abouts. Change it to something high such as 50505 or 54321. Close and restart ktorrent for ensure the change has taken affect. 6881 is sometimes blocked by ISP's to limit/block torrent traffic :(

A torrent download is a 2 way conversation; you download a bit, you upload a bit so you will want check your upload speed in the ktorrent options. You will want to set it about 50-60% of your total upload "bandwidth" - usually much much less than your download speed. For example if your total up speed is 50kb/s set the bandwidth available to torrents to 25-30kb/s. This will stop your torrents choking and leaves you a bit of speed to do other web browsing etc while your torrents run ;) Don't bother limiting your download speed as MOST torrent clients will throttle back their download speed when you download other files from the web / updates and then automatically ramp it up when you are done;)

Also have a look at the number of "seeds" available. 

Further to Rasa's explanation above a seed is someone else who has the completed files described in the torrent and is sharing them at the moment. You need seeds (usually) for the download to you to complete.

You may also see mention of "peers" they are people like yourself who are currently downloading the files but have not completed yet. They may have more of the files than you; they may have less. 

If you find you still have a problem then we might have to plumb the dark depths of port forwarding - but this is not always necessary.

I use use qbittorrent btw - jus' to throw another client idea in the mix :D

---

### Post by wolfen69 on 2011-10-25
> **3v3rgr33n said:**
> dude! i'm using KTorrent. everything i download ; the status is always --"stalled"

It may simply mean that there are no seeders available to get the file from.

---

