---
title: "Asunder not collecting track infomation for ripping"
date: 2020-06-16
forum: Multimedia Software
---

### Post by jukingeo on 2020-06-16
Hello All,

I have been looking for a decent CD ripping utility for Ubuntu Studio 16.04.  I have been trying two right now, one is Sound Juicer and the other is Asunder.   While I do intend to rip in several formats, obviously by and large, I am going to use the MP3 and MP4 formats. I have tried Sound Juicer first and it reliably gathers the CD information directly from the internet, however, the thing with Sound Juicer is that you have no control over the ripping quality.  There are no settings for the MP3 sample rate, so I do not know what the tracks are being ripped at.

Enter Asunder.  Ok, now with this ripping utility, I have much more control over the sound quality as I can select the bitrate.   I have decided to go with what is considered standard and I have set the bitrate to a fixed 192k.   (For critical work, I will go to 256k)  I have ripped the same tracks with both programs and while both sound good, I have to say the one that I recorded with Asunder does sound better and it has better stereo separation.   So giving that I recorded that one at 192k, I can conclude that Sound Juicer is sampling at a lower frequency.  Not good.   Ok, so with that in mind, I do want to use Asunder instead, BUT there is a BIG issue in that Asunder doesn't seem to be finding the track information, even after I hit the CDDB button it fails to get the information from the internet.

Another thing I have noticed is that Asunder doesn't offer a preview of the tracks.  I have to do this with another program.   Sound Juicer allows preview of the tracks.   That being said, of the two programs, it seems Sound Juicer is better with its interface, but the deal breaker is not being able to adjust the sound quality.

I am fine without the track auditioning feature on Asunder as my Parole player starts up automatically and I can preview the tracks there.  But the deal breaker for me with Asunder is not being able to find the track information.   If this issue could be fixed, then I would use Asunder.

I know some have recommended Ruby Ripper, but I heard that it takes a LONG time to rip disks.   Any suggestions and advice would be much appreciated.

Thank you,
Geo

---

### Post by Dennis N on 2020-06-16
The freedb.org database shut down on Mar. 31, 2020 so programs configured to use that can't find information. That may explain failure to locate any data. But, you should be able to rip the tracks anyway, then use Easytag to do a lookup on cddb by Album name and have it tag the files with the data. I had to do this a few days ago.

I use grip as the ripper and encoder. Very configurable. It's not in the Ubuntu repos, but I have it in Fedora. It now suffers from this problem too.

---

### Post by Yellow Pasque on 2020-06-16
Does musicbrainz still work? Maybe abcde would be a good ripper.

---

### Post by Yellow Pasque on 2020-06-17
You can probably change the cddb server to gnudb.gnudb.org in asunder's preferences ('Advanced' tab).

---

### Post by seebarn on 2020-06-21
> **Yellow Pasque said:**
> You can probably change the cddb server to gnudb.gnudb.org in asunder's preferences ('Advanced' tab).

Thanks YP - I hit this problem today after ripping hundreds of CDs in the past with Asunder, and your solution worked quick and easy!  Glad I found the thread quick - I recently updated both systems I rip on to Xubuntu 20.04 and I was ready to check just about everything but the obvious!

---

### Post by jukingeo on 2020-06-28
> **Dennis N said:**
> The freedb.org database shut down on Mar. 31, 2020 so programs configured to use that can't find information. That may explain failure to locate any data. But, you should be able to rip the tracks anyway, then use Easytag to do a lookup on cddb by Album name and have it tag the files with the data. I had to do this a few days ago.

I use grip as the ripper and encoder. Very configurable. It's not in the Ubuntu repos, but I have it in Fedora. It now suffers from this problem too.

What is Easy Tag?   

> **Yellow Pasque said:**
> You can probably change the cddb server to gnudb.gnudb.org in asunder's preferences ('Advanced' tab).

This seemed to work out, but only partially.  I grabbed 7 discs and it only found the information on 2 of the 7 discs, so this really isn't going to help too much as I HATE entering the information in manually.   It just takes too long.  Now I have noticed there was a port setting for the cddb server.  I just left the setting as it was (I think it was 8880), and it seemed to get the information on those two discs immediately.   Is there another, better and more updated server than gnudb.gnudb.com?  That server doesn't seem to have as much disc information.  I mean I grabbed 7 of my 700 CD's and only got the information on 2 of them?  No that isn't good.

Any other suggestions?

Thank you,
Geo

---

### Post by Dennis N on 2020-06-28
> What is Easy Tag?
[https://wiki.gnome.org/Apps/EasyTAG](https://wiki.gnome.org/Apps/EasyTAG)
And in the terminal:
```
apt show easytag
```

---

### Post by Yellow Pasque on 2020-06-28
>  Is there another, better and more updated server than gnudb.gnudb.com? 

"All official gnudb servers are running cddbp at port 8880 and http at port 80. The path for http-access is /~cddb/cddb.cgi" -- [https://www.gnudb.org/howto.php](https://www.gnudb.org/howto.php)

---

