---
title: "LTS Upgrade -- Tuner Issue"
date: 2012-08-27
forum: Mythbuntu
---

### Post by JWB47 on 2012-08-27
I have looked through various threads today and found some hints, but nothing seems to have helped.

*Background*

Over the last month or so, I have been updating my various systems to the latest version 12.04.1. First I updated the backend and all fromtends to mythtv 0.25. That seemd to go almost flawlessly. Then I updated one frontend from 11.10 to 12.04, other than lirc issues, this went well. Next I updated last week another frontend from 10.04.4 to 12.04.1. Again it seemd to go well (other than lirc).

Finally yesterday, I had a clear period with no critical recordings scheduled, so I updated the backend from 10.04.4 to 12.04.1. This upgrade did not go well!!

My backend consists of an intel based cpu (quad core) nvidia GT220 graphics, HVR-2250 for digital only and an HVR-950Q for digital and VCR analog access

Following the update, the mythbackend would not come up. This morning, I installed the latest firmware for the 2250, the 950Q seemed to be OK. The backend will eventually come up, but anytime I go into the frontend or setup, I get a message about being unable to connect to the backend. However, I am seeing the following on the backend.

```

$ ps ax | grep myth
 3916 ?        Sl     0:03 /usr/bin/mythbackend --syslog local7 --user mythtv

```At sometime earlier today, I got the backend to come up properly and did not get the message mentioned above. I am not sure what happened, but I had restored the database to the pre-upgrade state after I had deleted all the tuners to see if  I had to recreate them.

When that happened, I was able to view Recordings on the backend, but when I tried Live TV, I go the message "All Tuners are Busy". So I can't record anything either. I have found that I can play music, see the weather, browse videos and recordings look at the system status as long as I don't mind dismissing the dialog about not being able to connect to the backend all the time.

I should note that I tried to use mythtv-setup to delete the capture cards and recreate them. However, I couldn't as the process just hung. I believe this is relate to the "Tuners are Busy" state I was seeing.

I imagine it is some kind of configuration issue, but I have not been able to find any clues as yet.

My understanding is that the "Tuners are Busy" message is related to  permissions on the /dev/dvb/ device files, but to be honest, I am not sure how to  actually fix it. There is a suggestion in Bug #991130on how to fix the 950Q and another in the last couple of weeks about the 2250 that doesn't seem to solve the full problem.

The last bit of the mythbackend.log are here:

```

Aug 27 14:56:02 mmbe mythbackend[3916]: I CoreContext mythtranslation.cpp:66 (load) Loading en_us translation for module mythfrontend
Aug 27 14:56:02 mmbe mythbackend[3916]: N CoreContext main_helpers.cpp:556 (run_backend) MythBackend: Starting up as the master server.
Aug 27 14:57:02 mmbe mythbackend[3916]: I TVRecEvent mythdbcon.cpp:237 (Reconnect) MySQL reconnected successfully
Aug 27 14:57:02 mmbe mythbackend[3916]: I DBLogger mythdbcon.cpp:237 (Reconnect) MySQL reconnected successfully
Aug 27 14:58:17 mmbe mythbackend[3916]: I TVRecEvent mythdbcon.cpp:237 (Reconnect) MySQL reconnected successfully
Aug 27 14:59:33 mmbe mythbackend[3916]: I TVRecEvent mythdbcon.cpp:237 (Reconnect) MySQL reconnected successfully

```I realize there are probably several issues here, but if anyone can help  it would be appreciated.

Thanks

John

---

### Post by JWB47 on 2012-08-27
I have done some more investigation and I believe I have isolated the problem. It looks like I do not have the most recent firmware for the HVR-950Q. I removed it from the system, deleted all capture cards, and recreated the HVR-2250 cards. Prior to removing the 950Q, I was unable to even edit the cards in mythtv-setup.

I do not  know why yet, but the other problems seem to have gone away at the same time. I will investigate further as I try to get the 950Q back into operation.

In any event, I am marking this thread solved.

John

---

