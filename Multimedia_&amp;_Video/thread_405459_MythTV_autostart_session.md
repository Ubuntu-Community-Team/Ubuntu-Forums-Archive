---
title: "MythTV autostart session"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by castles on 2007-04-09
I installed MythTV over the weekend on Feisty using the guide that is [here]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend").

Its all working well but I had some issues with the tuner card and I got sick of rebooting and mythtv opening up first. So I turned off the mythtv automatic login (Made gnome default session).

Now that I have it all setup I want to make mythtv the default login again but its not in my sessions list.

So, how do I make myth the default again?

Thanks

---

### Post by tgm4883 on 2007-04-09
your link doesn't go to a guide, it goes to a post new thread.

but, I suppose you should do 

```
sudo gedit /etc/gdm/gdm.conf
```

change this 
```
AutomaticLoginEnable=false
AutomaticLogin=
```

to this

```
AutomaticLoginEnable=true
AutomaticLogin=mythtv
```

---

### Post by castles on 2007-04-09
ahh sorry.. I installed a stupid firefox plugin that copy's whatever you selected on a page to the clipboard.. should be fixed now.

I will try your suggestion at lunch..

---

### Post by superm1 on 2007-04-09
Edit your /home/mythtv/.dmrc.

It should look like this in the end:
```
[Desktop]
Session=mythtv-xsession

```

---

### Post by castles on 2007-04-11
I finally got around to trying this and it didn't work :( 

The error message I got was:

No Exec line in the session file: mythtv-session.
Running the Gnome failsafe instead

I didn't modify /home/mythtv/.dmrc. as it was already the same.

---

