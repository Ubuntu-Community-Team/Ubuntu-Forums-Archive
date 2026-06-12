---
title: "Multiple instances of Mythfrontend on boot"
date: 2008-05-06
forum: Mythbuntu
---

### Post by pssturges on 2008-05-06
Hi,

When I boot up my main backend/frontend machine, 2 instances of mythfrontend start instead of one. There are also multiple instances of a few other things including the network manager. It seems something is being run twice in the startup routine.

None of this is causing any huge problems, except that I have some stability issues if I don't close one of the frontends before playing any media.

I have no idea where to look to try & solve this. Is there any logs etc I should be looking at?

Thanks
Phil

---

### Post by superm1 on 2008-05-07
The easiest solution is to clean up your directories in ~/, .config, .cache etc.

Once you do, hit ctrl alt backspace to log out (don't log out the normal way as it will save active settings)

---

### Post by pssturges on 2008-05-07
Thanks for the reply.

Before I do something I might regret, when you say 'clean out', do you mean the entire contents of those folders? Also, when you etc, which others?

Thanks again,
Phil

---

### Post by pssturges on 2008-05-08
I gave it go and it worked! I renamed the .config & .cache folders so I had backups, then ctrl-alt-backspace and logged in again. All fixed. I did also need to reconfigure the auto login in mythbuntu control centre to get mythfrontend to auto start on boot, but thats it.

Cheers
Phil

---

### Post by Industrial on 2008-05-15
Hi all,

I've had a similar problem and tried clearing the .config and .cache directories as described above. Initially it seemed to work but the problem returned.

I'm finding that if I close the frontend (to browse a web page or whatever) when I try to reopen the frontend it goes through the regular page formatting progress sliders and then sits with the frontend background and nothing else. If I alt+tab at this stage sometimes I can see up to 5 instances of mythfrontend.real running but often just 1. If I leave it like this (overnight) the frontend(s) will eventually open completely and I can close any multiple instances but this is not very practical. Restarting X has no effect. The only way I can solve the problem is to do a full restart (very annoying if the backend is in the middle of recording something). After closing and opening the frontend a few times over the course of a day the problem returns.

Has anybody else seen this or know how to fix it?

System is Mythbuntu 8.04 AMD64. 2 x 320Gb SATA drives in LVM with a single partition that '/' is mounted on.

Thanks,

Ryan

---

### Post by robertjsharp on 2008-08-07
Hi,

I have the exact same problem so I checked what was going on in detail.

Seems that when I logged in (automatically) I had 2 instances of mythwelcome running. Interacting with the top instance was fine until I got to a point when the top instance handed lirc control over to something else (mplayer). Remote codes then seemed to get passed through to the second instance, starting another frontend.

Anyway - I killed everything, logged out with save session definitely NOT selected and logged back in. Result - just one mythwelcome running and everything OK. However, logging out with this instance running (regardless of the save sessions setting) seemed to result in two instances on the next login. 

Seems that the safe solution is to either kill all mythwelcomes before logout or never logout (let mythwelcome shutdown as it is supposed to). Only seems to get in this mess if I do happen to logout for some reason.

Could use a shell script to start mythwelcome but not sure this would solve the problem (would the desktop restart the script or the app that the script runs?). Real solution would be to change mythwelcome so that it exits if there is already an instance running (optionally). Perhaps I should suggest this to someone on the Myth dev team.

---

