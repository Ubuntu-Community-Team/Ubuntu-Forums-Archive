---
title: "Mythtv Openbox problems"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by Dubstar_04 on 2007-04-18
I've got mythtv set up just the way i like it and have been using it for just over 3 weeks. I'm using feisty and i kind of bodged together an install by using bits of 'how tos' from superm1 and simon parker.

I have a weird problem. when i use a gnome session and load mythtv the remote (mceusb2) is terrible its slow and misses the majority of button presses, however if i log into an openbox session the remote is fine, fast, and very responsive. However when i login to a openbox session i have no network connection unless i have already logged into a gnome session.

So basically i have two questions.

1. How do i make the remote more responsive in gnome, and
2. How do i get networking setup in openbox?

I tried adding 'exec NetworkManager' to the /usr/local/bin/mythtv.sh but this does nothing.

Your help will be appreciated.

Dubstar_04

Just to add i'm using a wireless network.

---

### Post by majoridiot on 2007-04-18
> **Dubstar_04 said:**
> 1. How do i make the remote more responsive in gnome...

make sure there is a symlink to your lircrc file in the mythtv user's directory... that seemed to help others.  assuming
your lircrc is located in your main user's home directory as .lircrc (which is the default install):

```
$ ln -s /home/<userdir>/.lircrc /home/mythtv/.mythtv/lircrc
```

(may or may not require sudo, depending on your permissions)

---

### Post by Dubstar_04 on 2007-04-18
I run my mythbox from the mythtv users directory and log in. In all honesty i'm more concerned why i can't get the wireless devices loading in the openbox session as I use the mythbrowser quite alot and i can't without logging out and then back into gnome, and then back into the openbox session to watch tv, because the remote is terrible in gnome.

Thanks for your help. This is gonna take some research to solve i think!!

---

### Post by Dubstar_04 on 2007-04-19
how do I start the network manager so it will login to my wireless network when using openbox?

this is the way forward as i never use the gnome interface anymore, my box logs into mythtv (openbox) session by default and i either watch tv or go on the internet (if i solve this problem).

I know i need to add something to the /usr/local/bin/mythtv.sh or mythtv.desktop files but what??

---

### Post by superm1 on 2007-04-19
> **Dubstar_04 said:**
> how do I start the network manager so it will login to my wireless network when using openbox?

this is the way forward as i never use the gnome interface anymore, my box logs into mythtv (openbox) session by default and i either watch tv or go on the internet (if i solve this problem).

I know i need to add something to the /usr/local/bin/mythtv.sh or mythtv.desktop files but what??
Network manager isn't exactly friendly for use with openbox, do you always connect to the same network?  

If you do, then login to your gnome session and choose network-admin.  Turn off roaming, and put in your information.  Reboot and things should come up fine in the openbox session.

---

### Post by Dubstar_04 on 2007-04-21
It worked!!!

After toying around with setting up a static network i seleted the DCHP option and away it went. just need to sort out the auto start up now and its done, and i can crack on with making my new theme.

Thanks for your help again, i would not of been able to get this far with out your guides and your help. 

regards,

Dubstar_04

---

### Post by superm1 on 2007-04-22
> **Dubstar_04 said:**
> It worked!!!

After toying around with setting up a static network i seleted the DCHP option and away it went. just need to sort out the auto start up now and its done, and i can crack on with making my new theme.

Thanks for your help again, i would not of been able to get this far with out your guides and your help. 

regards,

Dubstar_04
Glad things worked :)
If your working on a theme, let me know when you finish up.  I'm going to have an extra mythtv-themes-unofficial package for gutsy that i'm planning.

---

