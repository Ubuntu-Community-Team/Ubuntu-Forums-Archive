---
title: "Upgrading (migrating) to Mythbuntu"
date: 2007-10-23
forum: Mythbuntu
---

### Post by MonkeyKnifeFight on 2007-10-23
Ok. So I've got a current Myth box running Xubuntu 6.10 or older (I can't remember). I want to change over to Mythbuntu and keep my current recordings. My recordings are on their own partition, so I can change the OS without disrupting the video files. What is the best way to to keep my recordings in the DB and move to Mythbuntu?

I'm sure there are others who might be changing from Knoppmyth or some other myth install. Is there a process to save recordings so they show up in Mythbuntu? Could you just dump the DB and restore it after installing? I would think that mythbuntu adds its own stuf in there and I wouldn't want to overwrite that.

Any ideas?

---

### Post by napsilan on 2007-10-23
I was able to use apt to upgrade my mythtv box from 7.04 to 7.10 without any major problems.  You can not just copy the recording files over since I think there is some info stored in mysql about them as well.  My advice would be to try doing a dist-upgrade.  Mythbuntu is really just gutsy with mythtv installed, it uses the same repositories as standard ubuntu.  Also check the mythtv.org wiki for "backup up database"

---

### Post by superm1 on 2007-10-23
> **napsilan said:**
> Mythbuntu is really just gutsy with mythtv installed, it uses the same repositories as standard ubuntu. 

I'd tend to disagree with this *partially*. There is a lot of other stuff that goes on behind the scenes when you use the mythbuntu meta packages :)

---

### Post by napsilan on 2007-10-24
@superm1

I didn't mean any disrespect, you do an amazing job.  I know mythbuntu also avoids normal desktop stuff, sets up auto-login, mysql, mythbackend, and more that I don't know.  It's a credit to the mythbuntu team that it's all as simple as it is.  My main point was that they use the same repositories and the upgrade should be able to be done with apt.

p.s. Since I think many people don't have a keyboard on their main box, perhaps mythbuntu-control-center should be able to be run without gksudo.  I know visudo can fix it but having a more friendly way would be great.  Currently if I want to use it, I have to do so over ssh with X forwarding.

---

### Post by superm1 on 2007-10-24
> **napsilan said:**
> @superm1

I didn't mean any disrespect, you do an amazing job.  I know mythbuntu also avoids normal desktop stuff, sets up auto-login, mysql, mythbackend, and more that I don't know.  It's a credit to the mythbuntu team that it's all as simple as it is.  My main point was that they use the same repositories and the upgrade should be able to be done with apt.

p.s. Since I think many people don't have a keyboard on their main box, perhaps mythbuntu-control-center should be able to be run without gksudo.  I know visudo can fix it but having a more friendly way would be great.  Currently if I want to use it, I have to do so over ssh with X forwarding.
Thanks :)

That's a bit of the trouble: the balance between usability and security.  I'm really wary of setting up mcc to run with root permissions since it can break so much, and then the box can quite easily be broken in many ways.  You can open synaptic right from it w/o entering a PW again!

---

### Post by MonkeyKnifeFight on 2007-10-29
Ummm... ok. So what should I do? I'm totaly fine with pulling a table or two out and then restoring after I upgrade. I just wonder which table(s) are ones that I can safetly restore without messing up the new mythbuntu install, but keep my shows.

I'm not sure the official myth forums would help, since I think this is specific to mythbuntu installs.

---

