---
title: "Totem Movie Player - how do I clear history?"
date: 2006-11-14
forum: Multimedia &amp; Video
---

### Post by Desire on 2006-11-14
Question for anyone willing to help!  How do I clear hitory off of Totem Movie Player?  When I click under _Movie_ it will show the last five videos I downloaded!  This is bad because they were porn and I don't want the owner of this PC to know I went on porn!!  :o  For real!  Please help me.  I want to clear it for good so they don't find out of I'll look like a real pervert.  This isn't a joke.  Please help me.  I went under _EDIT_ and then _PREFERENCES_ but I couldn't find anything that clears the history!

---

### Post by yabbadabbadont on 2006-11-14
Strangely enough, it is stored with all the other recent files... regardless of application.  In gnome, Places->Recent Documents->Clear Recent Documents.  Then it should be gone.

---

### Post by Desire on 2006-11-14
Thank you!  :-D   You just saved me a lot of trouble and embarassmant.

---

### Post by yabbadabbadont on 2006-11-14
Whenever you use a computer that is not your own, always assume that EVERYTHING you do will be seen by the owner.  ;)

(for that matter, the owner will see everything when you use your own computer too :lol:)

---

### Post by mor on 2006-11-19
Clearing all recent files used to clear Totem history when I was using Dapper but it doesn't work for me in Edgy. Any ideas?

---

### Post by dmartinsca on 2006-11-20
In your home folder there should be a file named .recently-used, you'll need to edit that file removing all the blocks refering to totem.
EX:

Applications> Accessories> Terminal

dmartins@dmartins-laptop:~$ gedit .recently-used

```
<?xml version="1.0"?>
<RecentFiles>
  <RecentItem>
    <URI>file:///media/nfs/shared/TV/heroes.101.hdtv-lol.avi</URI>
    <Mime-Type>video/x-msvideo</Mime-Type>
    <Timestamp>1163999342</Timestamp>
    <Groups>
      <Group>Totem</Group>
    </Groups>
  </RecentItem>
  <RecentItem>
    <URI>file:///home/dmartins/downloads/LAB10a.doc</URI>
    <Mime-Type>application/msword</Mime-Type>
    <Timestamp>1163551428</Timestamp>
    <Groups>
      <Group>openoffice.org</Group>
      <Group>staroffice</Group>
      <Group>starsuite</Group>
    </Groups>
  </RecentItem>
</RecentFiles>
```

The block of text here you need to remove is:
```
  <RecentItem>
    <URI>file:///media/nfs/shared/TV/heroes.101.hdtv-lol.avi</URI>
    <Mime-Type>video/x-msvideo</Mime-Type>
    <Timestamp>1163999342</Timestamp>
    <Groups>
      <Group>Totem</Group>
    </Groups>
  </RecentItem>
```

---

### Post by andoty_jazz on 2007-03-16
Thanks a for deciphering the recently used xml. It would be helpful for us Ubuntu newbies.

---

### Post by waggingwabbit on 2008-04-19
is there a way to just disable recently used?

---

### Post by falconac on 2008-04-22
It would be great if we could just disable the history for Totem.  Otherwise it might not be great player for the, you know, legitimate and family-friendly videos we all watch.  Anybody have any ideas?

---

### Post by JohnJackson on 2008-06-16
A bit late, but this may be helpful to someone. You can delete the .recently-used file and create a directory of the same name. This way the .recently-used file can not be recreated, thus disabling the feature.

---

