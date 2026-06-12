---
title: "[SOLVED] banshee podcast"
date: 2008-11-15
forum: Multimedia Software
---

### Post by b0b138 on 2008-11-15
How do you remove a podcast? There is no remove or delete. Banshee 1.4.1

---

### Post by ukblacknight on 2008-11-15
If you mean remove a downloaded podcast, you can simply right click on it and click "Remove downloaded file(s)"

If you don't want to see old podcasts for instance, you can right click on one/a selection and chose "Mark as old".

---

### Post by mattman on 2008-11-15
I'm having trouble with podcast episodes disapearing before they even finish downloading. Which makes it hard to transfer to my mp3 player.

---

### Post by mattman on 2008-11-16
bump

---

### Post by b0b138 on 2008-11-16
> **ukblacknight said:**
> If you mean remove a downloaded podcast, you can simply right click on it and click "Remove downloaded file(s)"

If you don't want to see old podcasts for instance, you can right click on one/a selection and chose "Mark as old".

Yes, but its still there. I think I should have said unsubscribe.  

How do I unsubscribe from a podcast?

---

### Post by ukblacknight on 2008-11-16
> **b0b138 said:**
> Yes, but its still there. I think I should have said unsubscribe.  

How do I unsubscribe from a podcast?

You can right click on the podcast (under where it says "All Podcasts (n)", with your different subscriptions, and select "Unsuscribe and delete".

I'm using Banshee 1.4.1 though, I can't remember if that's available in 1.2.1!

---

### Post by b0b138 on 2008-11-16
hmmm... I dont have that option, all I got is subscribe to podcast and update podcasts.

---

### Post by ukblacknight on 2008-11-16
> **b0b138 said:**
> hmmm... I dont have that option, all I got is subscribe to podcast and update podcasts.

Sounds like 1.2.1 can't do that then... which is odd.  You may wish to update to Banshee 1.4.1.

You'll need to add the following repo's (System > Administration > Software Sources > Third Party Software > Add):

```

deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main

```

After it's reloaded, you should be notified of an update available.

---

### Post by b0b138 on 2008-11-16
im using 1.4.1, on hardy

---

### Post by ukblacknight on 2008-11-16
So you can't see this menu item, as seen in my screenshot?

---

### Post by ukblacknight on 2008-11-16
Sorry, forgot the screenshot, here it is...

---

### Post by b0b138 on 2008-11-16
nope :(

---

### Post by b0b138 on 2008-11-16
lol...something compelled me to add another podcast and after doing so I got all the menu options. So I added a few, then started removing them. But when it gets down to one, I lose the options again. Is this just me or should this be reported as a bug somewhere?

---

### Post by b0b138 on 2008-11-16
found the bug report [http://bugzilla.gnome.org/show_bug.cgi?id=560210](http://bugzilla.gnome.org/show_bug.cgi?id=560210)

---

### Post by ukblacknight on 2008-11-16
Ah, I've got a few podcasts so I can't re-create that bug, unless I unsuscribe to them.

It's probably a really simple bug, hope they fix it soon!

---

### Post by jimav on 2010-11-24
No!  The screenshot in post #11 shows the "Delete and Unsubscribe" feature which deletes *EVERY* episode and cancels the subscription!  

There does not seem to be any way to get rid of individual podcast episodes (e.g. after you have listened to them on your iPOD).   Except to delete all episodes including ones you have not yet listened to...

---

