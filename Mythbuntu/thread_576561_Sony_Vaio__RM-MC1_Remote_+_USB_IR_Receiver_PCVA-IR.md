---
title: "Sony Vaio  RM-MC1 Remote + USB IR Receiver PCVA-IR6U"
date: 2007-10-15
forum: Mythbuntu
---

### Post by govee on 2007-10-15
I initially tried to use the MCE (USB) as the default remote since the Vaio isn't listed. a few of the buttons worked but most didnt, ie channel up down caused a replay but "ok" does do select. I could not find any info to indicate if the MC1 was made by a different vendor and remarked Sony Like with much of Sonys speakers. Is there a direct Vaio RM-MC1 is the same as "****"?

---

### Post by superm1 on 2007-10-15
My recommendation here is to go through and run irw

See what buttons are recognized by lircd and which ones aren't.  Any buttons "not recognized", you'll need to find an improved lircd.conf to use for your remote (and file a bug :))

If the buttons are all recognized, it's a matter of modifying your ~/.lircrc and ~/.mythtv/lircrc to better reflect the mapping that you are interested in.

---

### Post by govee on 2007-10-27
Ran IRW and all keys were recognized. They were all correct as well. I am trying to understand the next step.I looked in the ~/.lircrc and ~/.mythtv/lircrc and I am not sure what to change. My problem for instance is:
When channel up or down are depressed on the remote a jumping command happens, not change of channels. Looking for direction????

---

### Post by superm1 on 2007-10-28
> **govee said:**
> Ran IRW and all keys were recognized. They were all correct as well. I am trying to understand the next step.I looked in the ~/.lircrc and ~/.mythtv/lircrc and I am not sure what to change. My problem for instance is:
When channel up or down are depressed on the remote a jumping command happens, not change of channels. Looking for direction????
Start out with the ~/.mythtv/lircrc

Open it up in a text editor and look at the different entries.  Here is an example:
```
begin
    remote = mceusb
    prog = mythtv
    button = Left
    config = Left
    repeat = 0
    delay = 0
end

```


Here is a breakdown of the lines:

**remote:**the remote name as in lircd.conf
**prog: **the program using this remote block
**button:** the button as listed in lircd.conf
**config:** what button its mapped to in the program

---

### Post by govee on 2007-10-28
I changed the ~/.mythtv/lircrc and the remote attempts to change the channel, is I see the channel selection screen at the bottom and it goes up and down with the channel buttons button it does not cause a channel change. I checked the keyboard up down and they do the same with no impact to the STB. I attempted to use the channel change script but do joy. I may be implementing the script wrong. I will do more searching for the correct use.

thanks

---

### Post by superm1 on 2007-10-28
> **govee said:**
> I changed the ~/.mythtv/lircrc and the remote attempts to change the channel, is I see the channel selection screen at the bottom and it goes up and down with the channel buttons button it does not cause a channel change. I checked the keyboard up down and they do the same with no impact to the STB. I attempted to use the channel change script but do joy. I may be implementing the script wrong. I will do more searching for the correct use.

thanks
Start a different thread for this issue.  Looks like the remote issue is taken care of though.  Don't forget to file a bug with the correct lircrc and all remote info.

---

