---
title: "Headless photo server, with local management"
date: 2014-10-23
forum: Multimedia Software
---

### Post by matthijs3 on 2014-10-23
Hi all,

I run Ubuntu on my NUC. On this installation I keep all my photos, all neatly organized.
I've been researching a lot on how to create a perfect situation to view these photos and find the best ones back easily.

What I would like is to also view these photos on my Mac with a photo management software (for instance Digikam). Ideally, this management software builds a local thumbnail database so I can easily browse my library, even when not connected remotely.

I should be able to tag photos with this software, and these tags should be synced with the server from time to time. The photo management software should not touch the photos themselves, so have only read-only access.

Probably somebody has some experience with such a setup?

My current idea is:

- using sshfs on Mac with read-only tag, use Digikam and sync its sqlite database using Dropbox. Ultimately I write a small script on the Ubuntu server that parses this sqlite to filter all starred photos out and create symlinks to these photos to be read by the Plex server for display on TV.

Thanks in advance!

---

### Post by tgalati4 on 2014-10-23
Have you looked into a server-based photo catalog such as [gallery]("http://galleryproject.org/")?

---

### Post by matthijs3 on 2014-10-24
Hi tgalati4

Thanks for your quick reply and for thinking with me :)

I did look into these solutions, but preferably I would not install Apache (or nginx, etc.) on the server. I'd like to keep the setup simple (it already runs Plex and SSH, I want to keep the amount of servers low).

I like the idea of running an actual application on my computer, versus using a browser-based solution. In my experience the desktop apps are more responsive.

Maybe that's not making sense, if so, please tell me ;)

---

### Post by tgalati4 on 2014-10-24
Does your TV have a USB port?  Wouldn't it be easier to just copy your favorites to a thumb drive?  That way, you have a backup of your favorites, and you can keep your digikam library on your Mac--which would be fastest.

---

### Post by matthijs3 on 2014-10-25
Hi tgalati4, thanks again for your quick answer!

USB would be a step back: our TV has a Chromecast dongle in it, which I can control using Plex (send photos to it from my server, using my phone).
I agree that keeping my library on the Mac would be fastest, but it's too big for my Mac. That's why all the photos are stored on the server. Also, that way Plex can access them.

My problem is that I don't have any favorites yet, and I'd like to select them :) 
What about installing digikam on the server and using X11-forwarding to my Mac?

---

### Post by tgalati4 on 2014-10-25
Yes, you can certainly do that, but graphical performance will make you tear your eyes out.  I would get a fast external drive with firewire or thunderbut and connect it to your mac and use digikam on the mac.  Then create a favorites directory on the mac external drive, share it, so your plex server can see it, mount it, and serve your photos to your TV.

Seems like a lot of work for a slideshow.  I would just make a USB stick.

---

