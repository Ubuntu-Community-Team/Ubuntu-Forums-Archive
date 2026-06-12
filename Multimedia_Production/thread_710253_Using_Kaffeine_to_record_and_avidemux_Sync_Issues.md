---
title: "Using Kaffeine to record and avidemux Sync Issues"
date: 2008-02-28
forum: Multimedia Production
---

### Post by caish5 on 2008-02-28
Hi all,

I'm currently using kaffeine to record DVB tv streams as .m2t files.
The recordings work fine but when i go into avidemux to edit out the ads and compress them a little for storage everything goes out of sync. I initially thoguht i could adjust this with the audio shift function but apparently it does nothing.
Anyone know how i can achieve a few AVI files without sync issues, Preferably in some GUI manner!

Thanks in advance

---

### Post by Creative2 on 2008-02-28
well maybe you can encode into avi with mencoder 

mencoder INPUT -idx -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000  -vf scale -zoom -xy 720 -xvidencopts fixed_quant=4 -o OUTPUT.avi

if you are in america replace 25 with 30 

if you don't want resize movie try to delete      -vf scale -zoom -xy 720 

idx meaning :

-idx : Rebuilds index of files if no index was found, allowing seeking.
              Useful with broken/incomplete downloads, or badly created files.
              NOTE: This option only works if the  underlying  media  supports
              seeking (i.e. not with stdin, pipe, etc).

also if you have other avi video with syncro problem you could try this 

mencoder INPUT -ovc copy -oac copy -forceidx -o OUTPUT

---

### Post by caish5 on 2008-03-01
ok i'll try that.
Any ideas on chopping the ads out?

---

### Post by Creative2 on 2008-03-01
i don't know what you mean with choppping the ads out but anyway 

with this you can encode only a part of your movie 

mencoder INPUT -ovc copy -oac copy -ss  hh:mm:ss.ms  -endpos hh:mm:ss.ms  -o  OUTPUT.AVI

if you look at this command line you can easly understand importants things are :
-ss  hh:mm:ss.ms  -endpos hh:mm:ss.ms
start time ------------endtime

so you can combine that options with your with example 

i will start to encode at 10s to 50 s' so i will encode only 40 seconds, 

mencoder INPUT -idx -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000 -vf scale -zoom -xy 720 -xvidencopts fixed_quant=4   -ss  00:00:10.00  -endpos 00:00:50.00            -o OUTPUT.avi

anyway i think avidemux is better to cut , then you can always resyncronize with this fast comand line

 mencoder INPUT -ovc copy -oac copy -forceidx -o OUTPUT

---

