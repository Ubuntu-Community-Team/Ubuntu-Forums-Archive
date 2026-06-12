---
title: "Yet an other Database version issue..."
date: 2014-02-07
forum: Mythbuntu
---

### Post by johnfm3 on 2014-02-07
Ok, I have a brand new Mythbuntu setup which was built from Ubuntu 12.04 32bit OS.  I have configured the myth backend setup using mythtv-setup an mythbuntu-control-centre so that this machine is the primary backend, has a frontend installed, an configured to allow frontends from other host's to connect as well.

When I connect to the backend from the frontend on the same box, the FE seems to connect with out issue.  An view the few movies I have added.

When I try to connect to the backend from mythtv on my netbook running OpenSuSE 13.1 64bit, I recieve the following error.  "This version of MythTV requires an upgraded database (schema is 18 versions behind)

The command prompt output following the command to start the front end on my netbook shows me the following error...
MythCoreContext:  Connecting to backend server: 192.168.2.7:6543 (try 1 of 1)
Protocol version or token mismatch (frontend=77/WindMark,backend=72/??)

My other test (which may be a seperate issue) is my Raspberry Pi running XBMC fails to connect with a error message about the pvr client not running.

Before everyone jumps on the band wagon, yes I have ran mythtv-setup as well as allowed the mythbackend to run.  Thats why I am here asking the questions.

Unless there is a reason to not upgrade to version 77, what does it take to do that?

Could really use some guidance on this.

John

---

### Post by blm-ubunet on 2014-02-08
You can get mythbuntu to 0.27+fixes by configuring mythbuntu control centre etc...
You can search the mythtv source code on git for the database schema/ API version..

But 0.27+fixes is also a moving target so you are always going to have problems maintaining compatibility.
Mythtv requires all FE & BE to be on the same API version.
Branch 0.27+fixes git is at schema 1317 & api protocol 77:
[https://github.com/MythTV/mythtv/blob/df5f9d29af0ac16552e6d70d8137658962831054/mythtv/bindings/python/MythTV/static.py](https://github.com/MythTV/mythtv/blob/df5f9d29af0ac16552e6d70d8137658962831054/mythtv/bindings/python/MythTV/static.py)

I've always had to build xbmc from source to get a version that was close enough to mythtv.

---

