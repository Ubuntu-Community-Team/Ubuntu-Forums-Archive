---
title: "hundreds of wifi login windows after laptopt closed"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by CameronWyse on 2013-04-14
Hi there,

Sure this is a settings issue, but if I have 12.10 64bit running on my laptop (lenovo G580 with a broadcom network card)

if i close my laptop for a while and then re-open it, the wifi connection re-establishes itself pretty quick and the whole experience works great.


however, if i have thunderbird running and do the same thing, when i open it i have hundreds (literally) of wifi login dialog boxes on the screens under network icon on the unity left hand side bar.
guessing it's thunderbird trying to connect to the internet to download messages during the time the laptop is closed, but only way i can get rid of all the dialog boxes is to logout and log back in.

i've had a look at hibernation/lid closing settings but can't see anything obvious

any help would greatly appreciated

thanks

Cameron

---

### Post by sauyon on 2013-04-14
You could use WICD instead of NetworkManager to avoid stupidity :P

[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

---

### Post by CameronWyse on 2013-04-14
actually, just realised it's nothing to do with Thunderbird. it happens if the laptop's lid is closed and it's left for a long time.

i'll give wcid a try and see how that goes

---

### Post by sauyon on 2013-04-14
I've never had that particular issue, but network manager likes to just keep trying and trying to reconnect to a network until you rage and kill wireless :P.

I assume that you want your laptop running when it's closed, right?

---

### Post by CameronWyse on 2013-04-15
i don't mind if it hibernates, as long as when i open it the network reestablishes itself...

i used to have an issue before where i'd shut the lid and have to logout and back in again to get the wifi to restart again as it used to say wireless not managed (or words to that effect)

i'll try hibernating first and see if that works ok

UPDATE:
the laptop's power settings are that it should suspend when the lid is closed (plugged in or not). hibernate option is grey'd out.
i switched my wireless off at the router yesterday and during that time i had constinual login prompts (even though the password was already in the dialouge box).

i guess if i switch off connect automatically, i'd have to manually (re)connect every time?

would it be throwing up dialogue boxes during the time when the laptop lid is closed (so the machine kills the network hardware?) but it's not in suspend mode yet so network manager is still trying to work as normal and regain connection, and when it can't, it throws up the dialogue box?

---

### Post by sauyon on 2013-04-15
That's strange...

My guess would be that your laptop isn't suspending correctly, but I honestly have no idea.

Could you tell me the results of
```
ifconfig
```
after you wake your laptop and wifi isn't working?

---

