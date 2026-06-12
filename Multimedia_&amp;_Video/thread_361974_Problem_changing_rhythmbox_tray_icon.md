---
title: "Problem changing rhythmbox tray icon"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by leeyee on 2007-02-15
Hi guys,

I know this question has been asked for hundred and thousand times. And I did do a lot of googles before the post. However, the problem still can't be resolved. And those ways I found are most based on Ubuntu Dapper.

I'm currently using Edgy, and I remember that under Dapper what I need to do was just changing icons under /usr/share/rhythmbox/art to my wantings. And it worked fine! 

After upgraded to Edgy, i found this way didn't work anymore, the tray icon didn't change after I changed icons under /usr/share/rhythmbox/art . And I also tried modifying icon themes, but they all didn't work. The icon theme I'm using is Tango, which was installed via apt-get. Any idea?

Any help will be highly appreciated! And hope I've made myself clear. Sorry for my English. ^_^

---

### Post by Waappu on 2007-02-15
Hi

Place same icon to ```
/usr/share/icons/gnome/22x22/apps/
```and name it ```
rhythmbox-tray-icon.png
```
then type in terminal```
cd /usr/share/icons/gnome
sudo gtk-update-icon-cache -f .;
killall gnome-panel
```

I'm not sure but you may need place that icon also to your current icon folder. E.g. if you use Human icon theme then but icon to```
/usr/share/icons/Human/22x22/apps/rhythmbox-tray-icon.png
```
and type in terminal```
cd /usr/share/icons/Human
sudo gtk-update-icon-cache -f .;
killall gnome-panel
```

---

### Post by leeyee on 2007-02-15
Hey, that's very good, it works!

And I didn't place the icon into other folders execpt this:
```
/usr/share/icons/gnome/22x22/apps/
```
Then did a icon cache update as normal, restart rhythmbox, it works! Thank you guy!:)

---

### Post by Waappu on 2007-02-15
Hi

Ok thats good.

Then we can do this way also

type in terminal```
ln -s -f --backup=off /usr/share/rhythmbox/art/rhythmbox-tray-icon.png /usr/share/icons/gnome/22x22/apps/rhythmbox-tray-icon.png;
cd /usr/share/icons/gnome;
sudo gtk-update-icon-cache -f .;
killall gnome-panel;
```

Now you have link and if you want change tray icon again just place it to```
/usr/share/rhythmbox/art
```

---

### Post by leeyee on 2007-02-15
Hey, how do you think of changing those icons in the rhythmbox GUI? For example, the podcast icon in the side panel? They all have icons under
```
/usr/share/rhythmbox/art
```
and change them didn't work. However, some icons for example the "Shuffle", "Browse" icon in the Tool Panel can be changed by copy desired icons to 
```
/usr/share/icons/Tango/24x24/actions
```
and then update the cache(I'm using Tango icon theme).

---

### Post by Waappu on 2007-02-16
Hi

I think some of are```
/usr/share/icons/gnome/24x24/stock/net/stock_channel.png
/usr/share/icons/gnome/24x24/stock/media/stock_music-library.png
/usr/share/icons/gnome/24x24/stock/media/stock_playlist.png
/usr/share/icons/gnome/24x24/stock/media/stock_smart-playlist.png
```

---

### Post by hihihi on 2007-02-18
thanks for help man,
it worked for me.

to change the podcast-icon:
paste your favorite podcast-icon to /usr/share/icons/gnome/24x24/apps/
and rename it to: rhythmbox-podcast.png
afterwards
$ cd /usr/share/icons/gnome/
$ sudo gtk-update-icon-cache -f .;

restart your rhythmbox and voila.

ciao

---

### Post by leeyee on 2007-02-24
yeah, all of them work fine now. I've got a nice rhythmbox look. Thanks a lot!

---

### Post by Dave_Connor on 2008-01-19
Thanks since I was using a custom icon set off of Gnome-look.org and all I had to do was replace the rhythmbox icon with /home/<name>/.icons/<icon theme name>/scalable/apps/ and replace an icon named "rhythmbox.png" and it updated right away.

---

