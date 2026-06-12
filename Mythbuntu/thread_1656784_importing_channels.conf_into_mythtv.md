---
title: "importing channels.conf into mythtv"
date: 2010-12-31
forum: Mythbuntu
---

### Post by sami8519 on 2010-12-31
Hi,

I am using dvb-apps and scan-s2 and I am not able to import channels into mythtv, with with the process always resulting in error. Also mythtv default scanning does not scan all the channels. What is the proper way you follow guys? Is there a specific command for searching channels compatible with mythtv? Also if someone could share with me the channels.conf for Hotbird13E and/or Eutelsat 9E, I would be grateful.:lolflag:

Thanks and Regards
Sami

---

### Post by williammanda on 2010-12-31
Where are you located? What cable service are you using?

---

### Post by sami8519 on 2010-12-31
> **williammanda said:**
> Where are you located? What cable service are you using?

Hi,

I am using satellite service, located in the Middle east.

Regards
Sami

---

### Post by microtechno on 2011-01-02
I wasnt able to import channels in either when setting up the back end, it wouldn’t pick up the DVB-T Transports.
I managed to get it to work by manually entering in the transports frequency and one or two of the other settings then letting it scan that.
This worked for me, although I have no idea if this well help at all for a satellite and its frequencies.

---

### Post by sami8519 on 2011-01-02
yes That will work but the problem is that it would not only scan the frequency I entered but any frequency it can find along its way as well. This is will make the channel list crowded for me with unwanted channels. There is also predefined list of frequencies but they seem to be too old.

Regards
Sami

---

### Post by microtechno on 2011-01-02
> **sami8519 said:**
> Hi,

I am using dvb-apps and scan-s2 and I am not able to import channels into mythtv, with with the process always resulting in error. 

Also if someone could share with me the channels.conf for Hotbird13E and/or Eutelsat 9E, I would be grateful.:lolflag:

Thanks and Regards
Sami

What error do you get and where? Could you post the error. When scanning on the back end or when you run the scan-s2? Cant see any channel.confs so far but shall keep looking.

Cheers

EDIT: Just been looking online, whats in [FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]/usr/shar/dvb/dvb-s/ can you find the information for the satelites?
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by sami8519 on 2011-01-02
Hi,

The error I get is when I try to import my channels.conf by entering this file path: it says like this" error parsing 1%" I dont know what does this mean, I googled it and some people had it as well.

yup in /usr/share/dvb/dvb-s/ I see configs files for satellites and I used to them to scan channels but I can import the channels.conf generated. I also used scan-s but same result.

regards
Sami

---

### Post by newlinux on 2011-01-02
> **sami8519 said:**
> yes That will work but the problem is that it would not only scan the frequency I entered but any frequency it can find along its way as well. This is will make the channel list crowded for me with unwanted channels. There is also predefined list of frequencies but they seem to be too old.

Regards
Sami

If nothing else works but this you can delete the unwanted channels after scanning if you don't want them.

---

### Post by sami8519 on 2011-01-02
sure I will keep that as a last resort. Thanks

Regards
Sami

---

