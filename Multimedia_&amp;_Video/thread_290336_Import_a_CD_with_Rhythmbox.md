---
title: "Import a CD with Rhythmbox"
date: 2006-11-01
forum: Multimedia &amp; Video
---

### Post by _asc_ on 2006-11-01
Hello!

In Dapper I have always used Banshee as my default music player but now that I have Edgy installed I want to give Rhythmbox a try.

The first thing I want to do is import a CD into the library. But when I right-click on the CD icon in Rhythmbox and choose "Copy to library" nothing happens.

When I start Rythmbox from the command line I get the following warning at startup
```

(rhythmbox:8311): Rhythmbox-WARNING **: Unable to start mDNS browsing: MDNS service is not running

```

And whenever I press the "Copy to library" button I get
```

(rhythmbox:8311): Rhythmbox-WARNING **: RBLibrarySource impl_paste called when gconf keys unset

```

Has anybody else experienced this problem and is there a solution?

---

### Post by doclivingston on 2006-11-02
Open the preferences (Edit->Preferences), go to the library tab and check the setting in the "Library Structure" section.

Rhythmbox should complain if you haven't set them, but for some reason it doesn't appear to be.

---

### Post by _asc_ on 2006-11-02
Hello doclivingston!

I checked the library tab and noticed that the library location was not set. This is strange, because I speciified that directory when I first started Rhythmbox.

Fortunately, it is working now. Thank you very much for your reply.

---

