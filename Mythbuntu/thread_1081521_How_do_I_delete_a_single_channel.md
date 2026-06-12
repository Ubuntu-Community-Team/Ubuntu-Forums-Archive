---
title: "How do I delete a single channel?"
date: 2009-02-26
forum: Mythbuntu
---

### Post by AKADAP on 2009-02-26
How do I delete a single channel in myth TV?
As far as I can tell, the channel editor only allows one to delete all the channels from a video source.

I have several HDHomeRun boxes, and I have found that the channel scan does a very poor job of identifying unencrypted channels with MythTV on Comcast cable. For example it found 67 channels when scanning with the encryption detection enabled, but I found 110 channels by scanning with the encryption detection disabled and manually checking all of the channels. Of course there are more than 100 additional encrypted channels I'd like to delete with no means of deleting them.

Even without the encryption issue, there are plenty of shopping channels and religion stations I'd like to delete.

---

### Post by theophile on 2009-02-26
Highlight the channel in the channel editor and press "D."

---

### Post by AKADAP on 2009-02-26
> **theophile said:**
> Highlight the channel in the channel editor and press "D."

Thankyou!
Where was this documented?
Any idea why they did not use the delete key?

---

### Post by theophile on 2009-02-26
Throughout MythTV, "D" is the delete key. Not sure why.

---

### Post by parker13 on 2009-02-27
Another option is to set the channel to not be visible. That way, if you do another scan the channels won't appear again!

In MythTV Setup, find the channel in the list, select it and uncheck the "visible" box. 

If you have a lot of channels, it may be easier to do it in SQL, eg:

```

mysql -u root mythconverg
select callsign, visible from channel;
update channel set visible=0 where callsign="Community";

```

---

### Post by utar on 2009-02-27
I find the quickest method to set if a channel is visible is to use mythweb.  Select setup and then database and you get a full list of channels where you can easily tick if you want them to be visible.

---

### Post by levlhed on 2009-05-10
mythweb?

check "visible"?

Where exactly are these now?  I just installed latest mythbuntu and I can not for the life of me find either of these.

I would like to make some channels "invisible" so they do not reappear in future scans.

---

### Post by tgm4883 on 2009-05-10
> **levlhed said:**
> mythweb?

check "visible"?

Where exactly are these now?  I just installed latest mythbuntu and I can not for the life of me find either of these.

I would like to make some channels "invisible" so they do not reappear in future scans.

```
http://BACKENDIP/mythweb/settings/tv/channels
```

Notice there is a "visable" column, just uncheck the box for each channel you don't want to see.

---

### Post by SiHa on 2009-05-11
> **tgm4883 said:**
> ```
http://BACKENDIP/mythweb/settings/tv/channels
```

Notice there is a "visable" column, just uncheck the box for each channel you don't want to see.

Now that's a good tip, thanks. I've never noticed that before, but it'll certainly save a bit of time next time I have to do a scan.

---

### Post by tgm4883 on 2009-05-11
> **SiHa said:**
> Now that's a good tip, thanks. I've never noticed that before, but it'll certainly save a bit of time next time I have to do a scan.

Yep, I use to manually delete the files too every time I did a scan.  What a PITA.

---

### Post by nickrout on 2009-05-11
> **tgm4883 said:**
> ```
http://BACKENDIP/mythweb/settings/tv/channels
```

Notice there is a "visable" column, just uncheck the box for each channel you don't want to see.

there is a delete box in mythweb too.

---

### Post by tgm4883 on 2009-05-12
> **nickrout said:**
> there is a delete box in mythweb too.

Yes there is, although if you use it and rescan your channels again later you will get all those channels back.  If you just make them not visable, then you will not run into that problem (although it will use more bandwidth as it still downloads the channel data for the non-visable channels)

---

