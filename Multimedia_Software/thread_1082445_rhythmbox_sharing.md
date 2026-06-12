---
title: "rhythmbox sharing"
date: 2009-02-27
forum: Multimedia Software
---

### Post by jackgu1988 on 2009-02-27
hi! i am trying to share my rhythmbox music over my 2 laptops using lan and i can't find out how. i only found 1 tutorial that didn't help because it said that i had to go to edit -> preferences -> sharing tab, but there is no sharing tab. :p any ideas how i can do it?

thank you!

---

### Post by ad_267 on 2009-02-27
I think you go to Edit -> Plugins, tick DAAP Music Sharing and then go to configure.

---

### Post by jackgu1988 on 2009-02-28
cool! that's how you do it... but i still can't see my files from my other pc! :(

---

### Post by ad_267 on 2009-02-28
The best explanation of the DAAP sharing I could find is here:
[http://www.freesoftwaremagazine.com/books/ubuntu_applications/rhythmbox](http://www.freesoftwaremagazine.com/books/ubuntu_applications/rhythmbox)

You have to specify the IP address and port of the other computer to connect to under Music - Connect to DAAP share. Have you tried that? Also make sure the DAAP plugin is enabled on both computers.

Edit:

I've just tried this out but rather than sharing the music in Rhythmbox I installed mt-daapd which runs as a daemon so rhythmbox doesn't have to be running and your music is always shared even if no one is logged on. If you want to try this then you need to install the mt-daapd package and then in your web browser go to [http://localhost:3689/](http://localhost:3689/) and enter username admin and password mt-daapd. Then you can select which folder to share and other options. You might have to restart the daemon by opening a terminal and entering: "sudo /etc/init.d/mt-daapd restart" or just restarting your computer.
Then on the client computer you just need to enable the DAAP plugin in rhythmbox and it should automatically find the shared music.

---

