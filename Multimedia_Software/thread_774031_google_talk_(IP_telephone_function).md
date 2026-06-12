---
title: "google talk (IP telephone function)"
date: 2008-04-29
forum: Multimedia Software
---

### Post by presston on 2008-04-29
I need google ip-telephone in ubuntu. i have skype, but not all my contacts have it.

Anybody knows how realize **this** function? (as text IM i configured pidgin)

---

### Post by llano on 2008-04-29
Actually, Pidgin supports Google Talk out of the box. No need to install additional software, just add a seperate account for your Google Talk contacts.

Specifically:
1. Go to 'Accounts' > 'Manage'
2. Add a new account. From the protocol drop-down menu select 'Google Talk'
3. Fill your necessary Google info and you should be good to go.

Cheers,
llano

---

### Post by presston on 2008-04-29
sorry, you did not read my post. 

> text IM (for google talk)i configured pidgin.

But there are NO function of IP telephonein pidgin, only mesenger, and i need voice communication, IP telephone function

---

### Post by presston on 2008-04-29
up. people, its impotart think for me. need your advice

---

### Post by foresto on 2008-04-29
According to the google talk [client matrix](http://www.google.com/talk/otherclients.html), your options of voice chat client are severely limited at the moment.  If google ever makes good on their plan to implement SIP (the protocol used by services like gizmoproject.com), that should change.

In the mean time, here are some interesting links:
[http://www.gtalk2voip.com/](http://www.gtalk2voip.com/)
[http://code.google.com/apis/talk/open_communications.html#realtime](http://code.google.com/apis/talk/open_communications.html#realtime)
[https://answers.launchpad.net/ubuntu/+source/ekiga/+question/7619](https://answers.launchpad.net/ubuntu/+source/ekiga/+question/7619)

It might be worth asking your contacts to get a SIP-based account somewhere, gizmoproject for example.  Free software like ekiga will work with those services.

---

### Post by presston on 2008-04-30
no hope:(

---

### Post by timo1023 on 2008-04-30
Looks like no luck with Wine, either:
[http://appdb.winehq.org/appview.php?iAppId=2398](http://appdb.winehq.org/appview.php?iAppId=2398)

---

### Post by presston on 2008-04-30
i tried ... right, no luck

---

### Post by rykel on 2008-06-22
Hi all,

It seems like there is still no answer to how we Ubuntu users can seamlessly receive a voicecall from GoogleTalk.

I have tested various clients and setup, and indeed it is a 2008 headache!

The closest and most promising client to receive voicecalls from GoogleTalk would be OpenWengo, so I truly hope that the project will achieve its next breakthrough.

Gizmo5 does work with GTalk2VoIP BUT refuses to allow calls using other SIP providers... and being CLOSED source, it means that no one can fork Gizmo5 so that it works with VoIPdiscount etc.

Has anyone ACTUALLY TESTED and USED any Linux client to voicecall GoogleTalk users successfully in Ubuntu WITHOUT the messy, half-baked interface/installation issues of Empathy or Jabbin?

Thanks for advising.

---

### Post by jerinjoy on 2008-06-28
I'm interested in this too. Here is a new thread about a new software that apparently works.

[http://ubuntuforums.org/showthread.php?t=819046&highlight=google+talk+empathy](http://ubuntuforums.org/showthread.php?t=819046&highlight=google+talk+empathy)

---

### Post by www.rzr.online.fr on 2008-06-29
Fell free to test jabbin from my repo :

[http://rzr.online.fr/q/jingle](http://rzr.online.fr/q/jingle)

---

### Post by Abhinavhardikar on 2009-02-08
> **jerinjoy said:**
> I'm interested in this too. Here is a new thread about a new software that apparently works.

[http://ubuntuforums.org/showthread.php?t=819046&highlight=google+talk+empathy](http://ubuntuforums.org/showthread.php?t=819046&highlight=google+talk+empathy)
Empathy does work!! It just needs a better GUI.;-)

---

