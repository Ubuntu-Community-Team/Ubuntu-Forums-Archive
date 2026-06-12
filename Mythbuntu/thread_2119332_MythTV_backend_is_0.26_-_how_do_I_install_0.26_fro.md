---
title: "MythTV backend is 0.26 - how do I install 0.26 frontend on another machine?"
date: 2013-02-23
forum: Mythbuntu
---

### Post by Old Jimma on 2013-02-23
Hi Community:

I have MythTV 0.26 installed on a nice old (1.5 years old) machine... both the backend and the frontend work fine on that machine.

On the old machine, the command

> mythbackend --version

yeilds

> 
MythTV Version : v0.26.0-78-gf35f899
MythTV Branch : fixes/0.26
Network Protocol : 75


I built a new computer yesterday, and installed precise 12.04.

I think that 12.04 uses 0.25 as the 'official' Mythtv distribution.

[COLOR="Red"]**So, since I have a mythbackend v0.26 installed on the new machine, I want to install mythfrontend v0.26 on the newly built machine.**[/COLOR]

How do I do this? :-k

The URL [[COLOR="Red"]**http://www.ubuntuupdates.org/ppa/mythtv_0.26?dist=precise**[/COLOR]]("http://www.ubuntuupdates.org/ppa/mythtv_0.26?dist=precise") shows how to update your repositories to install 0.26:

> 
sudo add-apt-repository ppa:mythbuntu/0.26 
sudo apt-get update


After doing that, when I look at synaptic, and file [COLOR="Red"]**mythtv-frontend**[/COLOR] it shows that v0.25 is the version that will be installed. 

[COLOR="Red"]**How to I make sure that mythfrontend 0.26 gets installed?**[/COLOR]

](*,)

I think this is an important point, since other posts show that when the frontend version on a 'fronend machine' is not the same as the version on a 'backend machine' there are conflicts in the MythTV database schema between the 2 machines that prevent the 'frontend machine from running.'

[COLOR="Red"]**So, how to I make sure that mythfrontend 0.26 gets installed to increase the chance that those conflicts do not arise?**[/COLOR]

Thanks! :)

Old Jimma from the Old Country

:popcorn:

---

### Post by cariboo on 2013-02-24
Bump for the move.

---

### Post by tgm4883 on 2013-02-25
> **Old Jimma said:**
> Hi Community:

I have MythTV 0.26 installed on a nice old (1.5 years old) machine... both the backend and the frontend work fine on that machine.

On the old machine, the command



yeilds



I built a new computer yesterday, and installed precise 12.04.

I think that 12.04 uses 0.25 as the 'official' Mythtv distribution.

[COLOR="Red"]**So, since I have a mythbackend v0.26 installed on the new machine, I want to install mythfrontend v0.26 on the newly built machine.**[/COLOR]

How do I do this? :-k

The URL [[COLOR="Red"]**http://www.ubuntuupdates.org/ppa/mythtv_0.26?dist=precise**[/COLOR]]("http://www.ubuntuupdates.org/ppa/mythtv_0.26?dist=precise") shows how to update your repositories to install 0.26:



After doing that, when I look at synaptic, and file [COLOR="Red"]**mythtv-frontend**[/COLOR] it shows that v0.25 is the version that will be installed. 

[COLOR="Red"]**How to I make sure that mythfrontend 0.26 gets installed?**[/COLOR]

](*,)

I think this is an important point, since other posts show that when the frontend version on a 'fronend machine' is not the same as the version on a 'backend machine' there are conflicts in the MythTV database schema between the 2 machines that prevent the 'frontend machine from running.'

[COLOR="Red"]**So, how to I make sure that mythfrontend 0.26 gets installed to increase the chance that those conflicts do not arise?**[/COLOR]

Thanks! :)

Old Jimma from the Old Country

:popcorn:

That is the correct way (installing that PPA and doing an apt-get update). Do you currently have mythtv-frontend installed on that machine? What version gets installed if you 'apt-get install mythtv-frontend'

---

### Post by Old Jimma on 2013-02-25
version 0.25 gets installed.

---

### Post by tgm4883 on 2013-02-25
> **Old Jimma said:**
> version 0.25 gets installed.

After adding the PPA, did you do an apt-get update?

What does this command return

```
rmadison mythtv-frontend
```

---

### Post by Old Jimma on 2013-02-26
Hi TGM:

the 

> apt-get update

completely solved the problem!

Time to make some popcorn!

Many, many thanks!
Old Jimma from the Old County

---

