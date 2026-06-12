---
title: "Removed dhclient3 accidentally, network disabled"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by toolmania1 on 2010-11-14
I accidentally removed the dhclient3 file.  I had ran chkrootkit and it said it was a possible suspicious file.  Once I rebooted, the network was disabled.

I am running off the Ubuntu cd by choosing trial.

How can I get dhclient3 back onto my installed Ubuntu?

---

### Post by puppywhacker on 2010-11-14
You can probably just copy the binary from the CD back to where you have mounted the harddisk containing your ubuntu installation. If you don't know where it is, you can probably find it at "places" on the left-top in the menu-bar

I do these things in a terminal, your filemanager may not have enough access-rights. Open a terminal at applications/accessories

```
sudo cp /sbin/dhclient3 /yourubuntumount/sbin/
```

To also restore the ownership and 
```
sudo chown root:root /sbin/dhclient3
sudo chmod 755  /sbin/dhclient3
```

to me, it seems easier if you do it the other way around, boot into your installation and copy the file from the CD, you end up copy-ing it like this.

```
sudo cp /media/cdrom/sbin/dhclient3 /sbin/
```

---

### Post by toolmania1 on 2010-11-14
Thanks for the help.

I tried what you suggested, but ran into permission problems and was not able to copy all of the files over.  So, I found some room on some cds and copied over what I needed to.  Then, I just reinstalled Ubutnu.

I am back up now.

I am going to search and / or post about what to do when jams like this happen.  For example, since I used windows for so long, I could system restore.  So, I am going to look for something like that in Ubuntu.

---

### Post by toolmania1 on 2010-11-29
This is actually solved.  I know I mentioned posting something about how to get out of jams.  I will not put that in this post as that is another topic.

---

