---
title: "Windows sharing inconsistent"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by Silvertones on 2010-01-17
This is not a big deal but thought I'd ask for opinions.
My Ubuntu computer is networked to my Windows XP computer. All in all it works fine. The name of the workgroup on the Win comp. is BOBO. On the Ubuntu comp. if I click on Places/network/windows network BOBO does not always show up. If I click on Places/connect to server use the drop down & set to windows share then enter the address of the Windows computer it connects fine. Once I access the shared file it then puts an icon on the desk top and I'm good to go.
Any thoughts?

---

### Post by Morbius1 on 2010-01-17
Other than the fact that Places/network/windows is trying to find everybody and Places/connect to server is trying to find only one, I don't know.

It  would be interesting to see if there are any problems if once you use the Places/connect to server method, you bookmark it in Nautilus once it connects. It will show up under "Places" in nautilus sort of like a "mapped drive" does in Windows. You could also rename it so it makes more sense.

---

### Post by Silvertones on 2010-01-17
It shows up both under places and on the desktop and works fine. Just have to do it each reboot.

---

### Post by Morbius1 on 2010-01-17
> Just have to do it each reboot

You have to re - bookmark it at each reboot?

The bookmark should be persistent

---

### Post by Silvertones on 2010-01-17
When I connect to server and then access the win shared folder it automatically shows up under places and on the desktop. When you say "bookmark" what do you mean? How to do that so it stays after rebot.

---

### Post by Morbius1 on 2010-01-17
When you click on the icon on the desktop it should open up Nautilus.

On the top taksbar of Nautilus is an item labeled "Bookmarks". If you click on that, and then the option "Add Bookmark" it will place an item under "Places" in Nautilus on the left panel.

---

### Post by Silvertones on 2010-01-17
DUH! Well that was easy.

---

### Post by Silvertones on 2010-02-24
I'm still seem to have problems. I can always connect to the Windows computer now that I've used the "connect to server" option and bookmarked the shared windows folders. My problem is inconsistent ability to view the shared folders on the Ubuntu machine. Sometimes it works & sometimes it doesn't. Can't find the pattern. When I fired up the computers this AM all was fine. I check a 1/2 hr later and get error " The network path was not found"
ALL TESTING IS DONE WITH THE UFW DISABLED.
Any thoughts would be appreciated.

---

### Post by Silvertones on 2010-02-24
I think I may have it worked out. Before when I opened network I would see "ubuntu & "windows network" inside the WN folder would be nothing. Now when I open places/network I see Ubuntu & John ( my two computers ) & WN. Inside WN is Ubuntu & John. And BOBO ( my workgroup ). Inside BOBO is Ubuntu & John

    What I did is change a few things in the Samba Conf file.
    [LEFT]1. workgroup = Changed to my workgroup name on the Win comp[/LEFT]
    [LEFT]2.  wins support = yes[/LEFT]
    [LEFT]3.  interfaces = changed this ti the static IP address range of the 2 comp.[/LEFT]
    [LEFT][/LEFT]
    [LEFT]Any comments good or bad appreciated.[/LEFT]
    [LEFT][/LEFT]

---

### Post by Silvertones on 2010-02-25
It's back to noy working this AM. I don't know what the heck is going on

---

### Post by dmizer on 2010-02-25
Edited erroneous post.

All I can suggest is to follow the directions in the 6th link in my sig.

---

### Post by Silvertones on 2010-02-25
Thanks dmizer. That worked but then came back after lunch and gone. This did work well and sticks . I was even able to create a couple other shared folders and map them quite easily. I had to go through this tutorial a second time when the first try didn't work. Syntax and capital letters issue. Once I paid close attention it went perfectly.

[http://ubuntuforums.org/showthread.php?t=202605&highlight=network+windows](http://ubuntuforums.org/showthread.php?t=202605&highlight=network+windows)

---

