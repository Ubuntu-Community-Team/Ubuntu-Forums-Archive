---
title: "Upgrade to 0.21, now external channel change no worky"
date: 2008-03-13
forum: Mythbuntu
---

### Post by Phydeaux on 2008-03-13
Had 0.20 with weekly builds working wonderfully.  Have a Dish 311 receiver and a PVR-150 with its blaster.  Prior to the upgrade, the pvr-150 would control the dish receiver to change channels using a perl script.  The perl script hasn't been touched, and works manually if i use channel-change.pl 430, it changes to channel 430.  Now not a thing happens when I change channels using live tv, the ir blaster doesn't even light up.  Where do I look to find whether it's even calling the script?  As far as I can tell, in the setup it still has the external script in /usr/local/bin.

---

### Post by volkswagner on 2008-03-14
Only guessing here.  Verify mythv user has permission to use the file.   Check the backend.log for errors while changing channels.

---

### Post by Phydeaux on 2008-03-14
Thanks for the info.  I checked the script and the group and owner was root.  This probably was the case before, but I changed it anyhow.  It did have proper permissions, but I chmod to 777 just in case.
Actually by looking at the mythbackend.log (not the frontend as I had done before) I found the error:
```

2008-03-14 20:09:41.856 Channel(/dev/video0)::TuneTo(S-Video 1): Error, failed to find channel.

```
It had S-Video in there, I put in the 1, neither worked.  I cleared it (this was in the input secton of mythsetup) and now it works fine.  I have my dish receiver hooked via s-video to the card.

---

### Post by Beezleblub on 2008-04-21
Hi Phydeaux, 

I am having the same problem. 
How exactly did you solve this ? 
What did you 'clear' in the input section of mythsetup ? 

I tried re-addign the card input and channels, but no help :(
would appreciate if you can clarify how you did solve this ! 

Thanks.

---

### Post by aaltieri on 2008-04-27
I'm having a similar issue.  I updated a while ago, but rarely watch TV on the server.  When I tried to use the channel controls on the server tonight, nothing happened.

It changes channels brilliantly from the two Mac front ends though.  I tried re-installing Myth Frontend on the system to no avail.

The guide still works, as do the menu commands.  But that's about it.  It still records on various channels no worries as well.

Oh yes, Mythtv 0.21, with a PVR-150 and PVR-500.  I can only change tuners through the menus, I can not hit my programmed key and do it anymore.

Any ideas would be most appreciated!

Peace


--anthony

---

### Post by Beezleblub on 2008-04-28
I fixed my problem. 

start the backend setup 
go to input connections
select the appropriate input for your card
Set 'Preset tuner to channel' as BLANK

after that channel change is working again for me. 

this means now the TV always starts at the last viewed channel.

Lost the link with the explanation on why this happens, but was some work around for a bug in 0.21.

---

