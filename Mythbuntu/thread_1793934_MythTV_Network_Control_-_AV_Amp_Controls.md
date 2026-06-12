---
title: "MythTV Network Control - AV Amp Controls"
date: 2011-06-30
forum: Mythbuntu
---

### Post by tobiz on 2011-06-30
I'd like to be able to control my Marantz SR5002 AV amp volume etc from MythTV Network Control. The SR5002 is connected to MythTV via HDMI, it handles all audio passing on video over HDMI to the TV. I can control the SR5002 from Linux via its RS232 port using a Python script I've written. I'd like to call that script (in MythTV) when the appropriate button is used on my Network Remote device (Mythmote).  Any thoughts as to how this can be done? Is the Network Control 'jump table' "programmable"? If so where is it located and what's the format?

---

### Post by tobiz on 2011-07-04
> **tobiz said:**
> I'd like to be able to control my Marantz SR5002 AV amp volume etc from MythTV Network Control. The SR5002 is connected to MythTV via HDMI, it handles all audio passing on video over HDMI to the TV. I can control the SR5002 from Linux via its RS232 port using a Python script I've written. I'd like to call that script (in MythTV) when the appropriate button is used on my Network Remote device (Mythmote).  Any thoughts as to how this can be done? Is the Network Control 'jump table' "programmable"? If so where is it located and what's the format?
Doesn't seem too much interest in this proposal.  However, one solution is to run a server on the MythTV frontend which intercepts the Network Control commands and send those which could control the AV amp to it, passing on the remainder to the Network Control port; not probably the best solution, but it works.  Just in case anyone is interested, my Python code to do this is attached.  It could be improved, eg a config file to control which commands it interprets and what it calls to do so, in my case it's a call to a RS232 I/F Python script.

---

