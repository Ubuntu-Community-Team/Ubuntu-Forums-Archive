---
title: "remote control your music"
date: 2012-05-27
forum: Multimedia Software
---

### Post by macmaximus on 2012-05-27
I want control my music application on pc with my ipad. I have a computer with ubuntu 11.10. My music library is pretty big, more than 20,000 songs.
Normally, without remote, I use Rhythmbox. I like this apllication, but remote control in Rhythmbox with the advent of gnome 3 is no longer possible (is this true?). Now I'm looking for an alternative, a music application with remote control on Ipad. I tried, so far a couple of solutions, but not succeeded. Large libraries are often a big problem in applications.

---

### Post by roelforg on 2012-05-27
I use vlc on the computer and vlcamigo on my iphone.
This is how i installed and setup vlc (i assume your local ip is 192.168.0.xxx):
```

sudo apt-get install vlc libavcodec-extra-53

```
Then i added (i have ip addresses in the 192.168.0 block)
```

192.168.0.0/16

```
to /usr/share/vlc/lua/http/.hosts

Then i open vlc and click on view->add interface->web interface
Now i open vlcamigo on my phone and wait for it to detect my computer, click the item and there i go!

---

### Post by macmaximus on 2012-05-28
thank you Roelforg,

I managed to get it work. There still some issues to sort out, like: `can I  put vlc in shuffle mode from vlcamigo?` or `can I have multiple playlists in vlc?` or `can I create a library in vlc?` 
But thanks for your help, I'm getting somewhere.

---

