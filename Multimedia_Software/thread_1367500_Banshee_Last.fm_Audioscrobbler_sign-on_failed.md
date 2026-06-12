---
title: "Banshee: Last.fm Audioscrobbler sign-on failed"
date: 2009-12-29
forum: Multimedia Software
---

### Post by mashedbear on 2009-12-29
I've recently noticed that audioscrobbling to my Last.fm account from banshee has stopped working. This has been working fine for over a year.  I've not changed my last.fm password.

I've checked that banshee is authorised to access my Last.fm account - using the account settings dialogue in banshee and this all appears correct. My Last.fm account shows that banshee has been granted access to my account.  

However the banshee log file (found in ~/.config/banshee-1) says that sign to last.fm has failed. And tracks are not added to my recently played list in banshee - ie aduioscrobbling is not working


```
[[Warn  20:22:11.697] Audioscrobbler sign-on failed - Last.fm username is invalid or Banshee is not authorized to access you account.
[Warn  20:27:14.246] Caught an exception - The request timed out (in `System')
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] 
  at Banshee.Metadata.MetadataServiceJob.GetHttpStream (System.Uri uri, System.String[] ignoreMimeTypes) [0x00000] 
  at Banshee.Metadata.MetadataServiceJob.GetHttpStream (System.Uri uri) [0x00000] 
  at Banshee.Metadata.Rhapsody.RhapsodyQueryJob.Run () [0x00000] 
  at Banshee.Metadata.MetadataServiceJob.Run () [0x00000] 

```

Any ideas how to fix this problem? Can I check or edit the last.fm account settings that banshee is using via a config file? (the account settings dialogue doesn't let you do this. I am sure it did a few versions back).

thanks

---

### Post by boombox1387 on 2010-01-09
Which version of Banshee are you using?  If you're still using 1.5.1 or earlier, I would highly recommend upgrading to 1.5.2 (or even better, the [Daily Build PPA]("https://launchpad.net/~banshee-team/+archive/banshee-daily").  A lot of changes were made related to Last.fm integration after the 1.5.1 release.

If you're using a newer version of Banshee (or even if you're not) this sounds like something that should be reported to Banshee developers through their [bug tracking system]("https://bugzilla.gnome.org/browse.cgi?product=banshee").

---

### Post by mashedbear on 2010-01-14
I am using Banshee 1.6 Beta 3 (1.5.2)

---

### Post by boombox1387 on 2010-01-14
> **mashedbear said:**
> I am using Banshee 1.6 Beta 3 (1.5.2)

The authorization process changed between 1.5.1 and 1.5.2 (I think).  In more recent versions of Banshee (including 1.5.2, I think), Last.fm configuration has moved in to the main preferences dialog, and the authorization process requires visiting a Last.fm page that allows Banshee to connect to your account.

If you haven't done this, go to: Edit > Preferences > Source Specific [the tab] > Last.fm [from the drop-down box].  If Banshee is set up correctly with your account, you should see your last.fm username in a text field with an unclickable button next to it that says "Authorize."  If that isn't what you see, follow the instructions there to connect with your account.

Hopefully this helps.  If you've already done this (or doing so doesn't fix your problem), I'll gladly try to help more, but you might have better luck posting your question on Banshee's mailing list or filing a bug in their bug tracker.

---

### Post by mashedbear on 2010-01-14
OK checked the banshee bug tracker - and found a bug already reported and a solution!

So now solved by following the steps here [https://bugzilla.gnome.org/show_bug.cgi?id=603625]("https://bugzilla.gnome.org/show_bug.cgi?id=603625")

Thanks to boombox1387

---

### Post by Pseudo-Morph on 2010-07-24
> **mashedbear said:**
> Thanks to boombox1387

Thanks also to you for linking to this. :)

---

