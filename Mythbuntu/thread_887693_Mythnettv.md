---
title: "Mythnettv"
date: 2008-08-12
forum: Mythbuntu
---

### Post by wombo on 2008-08-12
[http://www.stillhq.com/mythtv/mythnettv/](http://www.stillhq.com/mythtv/mythnettv/)

Has anyone managed to get this running in Mythbuntu?

I keep getting the following error when running it from /home/htpc/mythnettv-release-3/

```
Traceback (most recent call last):
  File "./mythnettv", line 13, in <module>
    import gflags
ImportError: No module named gflags

```

---

### Post by kbarter on 2008-08-12
I was able to get it all installed.  I went to the google website to get the gflags stuff.

Here is what I did:
download and install [http://google-gflags.googlecode.com/files/libgoogle-gflags0_0.9-1_i386.deb](http://google-gflags.googlecode.com/files/libgoogle-gflags0_0.9-1_i386.deb)
download [http://google-gflags.googlecode.com/files/gflags-0.9.tar.gz](http://google-gflags.googlecode.com/files/gflags-0.9.tar.gz)

tar xvf gflags-0.9.tar.gz

Then go into the python directory, and run the install program there.

Unfortunately, I do not remember the exact steps, but the above can get you started.

---

### Post by wombo on 2008-08-13
Thanks, I had only installed the DEB file.

---

### Post by wombo on 2008-08-13
Just thought you all might be interested.

I found a bug in the code if you remove a subscription (IE make it inactive) it will continue to download when you run --update.

I had to edit the following on line 492 of mythnettv

From
```
for row in db.GetRows('select * from mythnettv_subscriptions'):
```

To
```
for row in db.GetRows('select * from mythnettv_subscriptions where inactive is NULL'):
```

Thanks

---

### Post by nickrout on 2008-08-13
> **wombo said:**
> Thanks, I had only installed the DEB file.

unfortunately the gflags .deb file does not include  the python component of gflags.

---

### Post by mikalstill on 2008-08-20
Hi folks. I am the author of MythNetTV, and am flattered that you are using it. In the future it would be cool if you could let me know when you find bugs, because I am otherwise unaware of them. You can do that at [http://www.stillhq.com/mythtv/mythnettv/](http://www.stillhq.com/mythtv/mythnettv/) or by sending email to the users list at [http://lists.stillhq.com/listinfo.cgi/mythnettv-stillhq.com](http://lists.stillhq.com/listinfo.cgi/mythnettv-stillhq.com) -- additionally this list gets updates when new versions of MythNetTV are released.

Regarding the gflags problems, I have removed gflags from the latest release to resolve this problem. When I get around to rearranging how the command line arguments work, I will reinclude it in a more planned manner.

Regarding the --update problem, I have rolled this fix into the current development version.

Cheers,
Mikal

---

### Post by nickrout on 2008-08-20
great to see the mailing list, i do recall emailing you mikal when I couldn't get it to work, got no reply and i gave up. Still keen to get it going though.

---

### Post by wombo on 2008-08-21
It would be good if we could make this part of mythbuntu

---

### Post by mikalstill on 2008-08-21
> **nickrout said:**
> great to see the mailing list, i do recall emailing you mikal when I couldn't get it to work, got no reply and i gave up. Still keen to get it going though.

That's a fair comment. I have hundreds of unread email messages at the moment, and spam makes it hard to find the ones I should be responding to. I'm hoping the mailing list will improve this by giving me a central place to look, as well as a place for people to support each other when I am unavailable.

Mikal

---

### Post by tgm4883 on 2008-08-21
> **wombo said:**
> It would be good if we could make this part of mythbuntu

Working with mikalstill to make this a possibility.

---

### Post by tgm4883 on 2008-09-22
There is a mythbuntu-testing PPA, mythnettv (and mythnettv-gui) are included in that PPA.

---

### Post by compbrain on 2009-08-26
If anyone is still looking for it, I build a python-gflags deb for Jaunty in my PPA. [https://edge.launchpad.net/~compbrain/+archive/ppa/](https://edge.launchpad.net/~compbrain/+archive/ppa/)

---

