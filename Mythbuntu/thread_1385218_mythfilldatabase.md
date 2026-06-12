---
title: "mythfilldatabase"
date: 2010-01-19
forum: Mythbuntu
---

### Post by mythbuntu101 on 2010-01-19
Hi,
 
I just installed Mythbuntu Back/Frontend configuration option.
 
mythfilldatabase seems to not stop or is in a constant loop attempting to connect to a web service.
 
1) what is the webservice mythfilldatabase  is attempting to use?
2) what is the function of mythfilldatabase ?
3) is mythfilldatabase trying to populate my schedulesdirect.org Lineup?
4) mythfilldatabase  ran several attempts to unsuccess (I tried many times to run mythfilldatabase ), can this cause further problems in the future and should I do a clean install altogether?

---

### Post by azmyth on 2010-01-19
1. You need to set this up for what service you want to use. If you're in the US, this is typically schedules direct. Assuming you're signed up and paid for and you set it up to use SD in mythtv-setup.
2. Populate the db with guide data.
3. If you set it to use this.
4. No I wouldn't do a reinstall. Your db just won't get populated. Once you set it up correctly it'll populate when run again.

Sounds like you haven't set it up as you'd remember if you had completed this step.

---

### Post by cnollet on 2010-01-19
Also, mythfilldatabase runs many times (once per each channel you're supposed to receive, I believe). So while it looks like its in a loop, its really just getting each channel per pass.

Additionally, the last time I set it up, I believe I saw a brief error flash by per channel, but then the program downloaded the channel data anyway.

---

### Post by mythbuntu101 on 2010-01-28
I too have a problem w/ 'mythfilldatabase' (mythbuntu 9.10) Can you supply a 'step-by-step' how to for this? SchedulesDirect info is okay. Here's their direct reply.
- - - - - -
MythTV downloads data in raw format and doesn't have the limitation. Since you can download data using XMLTV there's nothing wrong with yourSD account or PC setup, you must have a MythTV config issue. Unfortunately, we're not really in a position to help with applicationproblems. I don't even use Myth myself. I suggest you post on theMyth-Users mailing list. I'm sure there are folks there who can help.
 - - - - -
Can you provide how fix this MythTV config ? [http://mythbuntu.org/installation_manual](http://mythbuntu.org/installation_manual) is not currently working

---

### Post by azmyth on 2010-01-28
[http://www.mythtv.org/docs/mythtv-HOWTO-9.html#ss9.1](http://www.mythtv.org/docs/mythtv-HOWTO-9.html#ss9.1)

Scroll down to "General" and start from there.

---

