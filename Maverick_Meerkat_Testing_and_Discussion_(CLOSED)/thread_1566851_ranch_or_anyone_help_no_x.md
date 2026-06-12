---
title: "ranch or anyone help no x"
date: 2010-09-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2010-09-02
just again tried to update to 10.10 i can only login with no graphic display and cant get past that i get error no display specified. any ideas how to fix i am running in live 10.04 cd. can reinstall `10.04 no problem but as last resort. any ideas. install went fine until i restarted cant even go down to previous kernel and make that work. and fixes and how to do. this is nuts i have been testing ubuntu versions for over  years and never ran into this problem.i could drop down to prompt shell and enter something to fix but have no idea what command to run. since this i labor day weekend have time to play with and not in panic mode. i can alway reinstall 10.04 have separate partitions for home etc so no big deal but would really like to try and fix/tks

---

### Post by rburkartjo on 2010-09-02
just an idea what could i run from the command prompt.eg login and password

to maybe try to repair

---

### Post by ranch hand on 2010-09-02
Can you boot to recovery?  I find that a lot of upgrades can use a boost from the dpkg option.  I like it as it seems to have a little more force behind it than running dpkg --configure -a does.  And of course it looks for any thing it can upgrade (sometimes not a real good thing but you have the option of saying no).

If you can't get there I would hammer on dpkg in the terminal a bit.  Should give you some messages anyway.

If you use Nvidia dards you might want ot look at some of those threads, seems a little dicey.  If you had drivers installed it would probably be good to remove them and see if you can boot to low graphics and then follow the advice for your card (I bet it is on here).

As I use an ATI card and OSS drivers I am no help at all on that stuff.  The only thing I found with the ATI driver was that it;
A>didn't work as well as the OSS driver
B>better be removed before upgrading and reinstalled after.

---

### Post by ktp on 2010-09-03
> **rburkartjo said:**
> just an idea what could i run from the command prompt.eg login and password

to maybe try to repair

I would login and try removing xorg config file, if you have one.  That should kick in the vesa driver and give you graphic.

---

### Post by VMC on 2010-09-03
> **rburkartjo said:**
> just again tried to update to 10.10 i can only login with no graphic display and cant get past that i get error no display specified. any ideas how to fix i am running in live 10.04 cd. can reinstall `10.04 no problem but as last resort. any ideas. install went fine until i restarted cant even go down to previous kernel and make that work. and fixes and how to do. this is nuts i have been testing ubuntu versions for over  years and never ran into this problem.i could drop down to prompt shell and enter something to fix but have no idea what command to run. since this i labor day weekend have time to play with and not in panic mode. i can alway reinstall 10.04 have separate partitions for home etc so no big deal but would really like to try and fix/tks

Do you have a 10.10 livecd? It appears your trying to get to 10.10 through updating 10.04 or did I read your message wrong?
Also what hardware do you have, nvidia.

---

### Post by prshah on 2010-09-03
> **rburkartjo said:**
> cant get past that i get error no display specified.

Do you mean "no displays found" error? That kind of error is subsequent to some other failure during load of X. To know what other failure, please check (or post) your /var/log/Xorg.0.log file.

---

### Post by rburkartjo on 2010-09-03
just an idea since i have sometime until monday if i keep running the command sudo apt-get update && apt-get upgrade will the x problem be solved by updates. also what is the correct command to make sure i get all the updates form the non graphic mode/tks

---

### Post by rburkartjo on 2010-09-03
i just want to make sure i can install the new beta release from the non graphic terminal

---

### Post by ranch hand on 2010-09-03
If some packages are held back there is, of coarse "apt-get dist-upgrade" watch your butt.  May want to remove things you do not want removed.

---

### Post by rburkartjo on 2010-09-03
ranch and all who answered this thread tks. still cant get x to work. if someone can come up with a solution that i can get to work would appreciate.
really want to get it to work. installed fine except for the x problem and that is major. if i cant will have to go back to 10.04 sunday night or monday. i have to get this computer working for my daughters school work. just thought it would be neat to try out 10.10 and as mentioned before have done this successfully with most ubuntu  alpha and beta versions. ya'll all have a great labor day weekend. going camping with the family will check this thread when get back

---

### Post by ronacc on 2010-09-03
does x work from the live cd ?

---

### Post by rburkartjo on 2010-09-05
tks ya'll last update fix x now running 10.10

---

