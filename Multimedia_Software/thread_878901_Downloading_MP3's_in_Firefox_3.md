---
title: "Downloading MP3's in Firefox 3"
date: 2008-08-03
forum: Multimedia Software
---

### Post by neilrizo on 2008-08-03
Can somebody please help me out with this...

I've been trying to download an MP3 file from a file sharing service but I've been encountering a problem. The thing is whenever I click on the "Download" button it always opens up XMMS instead of downloading the file.

The funny thing is this is happening even if in the preferences section of FF3 all MP3 types are set to "Save File" as its corresponding action.

What's going on? How can I remedy this?

---

### Post by spin2cool on 2008-08-03
in Firefox 3, go to Edit > Preferences > Applications

search for 'MP3', then change the associated action to "always ask" (or "save file", if you prefer).

---

### Post by neilrizo on 2008-08-03
> **spin2cool said:**
> in Firefox 3, go to Edit > Preferences > Applications

search for 'MP3', then change the associated action to "always ask" (or "save file", if you prefer).


I appreciate the reply, but as my earlier post says the associated action in Firefox is already set to "Save file".

I've also tried setting it to "Always ask" but I still get the same results. It still gets opened by XMMS instead of being downloaded.

---

### Post by pbpersson on 2008-08-03
This is a silly question, but have you tried right-clicking on the link and choosing "save link as"?

---

### Post by neilrizo on 2008-08-03
> **pbpersson said:**
> This is a silly question, but have you tried right-clicking on the link and choosing "save link as"?

It's not silly at all. But the thing is it isn't a link, Rapidshare uses a download button. So I really have to click on the button for the action to occur.

---

### Post by spin2cool on 2008-08-03
> I appreciate the reply, but as my earlier post says the associated action in Firefox is already set to "Save file".

Sorry - my bad.

Run "firefox -ProfileManager" and try doing the same d/l using a clean profile.  If that works, it's something screwy in your installation, probably due to an extension/addon.

---

### Post by loboc on 2008-08-03
In the firefox download manager window (CTRL+y or Tools>Downloads)  you could look at the properties of the transfer and then copy past the source to a terminal download

```
 wget http://theserver.yourmp3ison.com/folder/fille.mp3
```

---

### Post by kostkon on 2008-08-03
> **loboc said:**
> In the firefox download manager window (CTRL+y or Tools>Downloads)  you could look at the properties of the transfer and then copy past the source to a terminal download

```
 wget http://theserver.yourmp3ison.com/folder/fille.mp3
```
If thi is RapidShare we are talking about, you cannot use *wget*, unfortunately.

---

### Post by Clark_Culver on 2009-09-06
I was having the same problem while trying to download the TWIT podcast.  It was driving me nuts.  The problem is with the VLC Multimedia plugin that is included by default with Ubuntu.  Disable it and the usual dialog will appear that will allow you to choose what to do with the file.  

Goto: Tools -> Add-ons -> Disable VLC -> Restart Firefox

- CC

---

