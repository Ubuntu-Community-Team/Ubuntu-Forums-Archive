---
title: "No sound from mplayer as a service"
date: 2015-02-24
forum: Multimedia Software
---

### Post by mark199 on 2015-02-24
I am currently setting up a new machine on which I have installed Ubunto 14.04.

For some years I have been using mplayer on a Suse machine as a radio alarm by adding or deleting a respawn line on the inittab. This way if the stream is lost at any time and the process dies, it is automatically re started.

On the new machine I have created a service for this and when I start the service the mplayer process runs fine but I get no sound out and on the sound setting gui it shows no running application. If I issue exactly the same command on the command line it plays OK. 

What am I missing?

---

### Post by TheFu on 2015-02-25
Access to the sound system is limited to actual console logins.  There are many reasons for this.
The workaround is to add the userid running the process thru cron/init to the **audio** group.

This is just a guess, but it worked for me to remotely manage my HTPC (connected to a household sound system).

---

