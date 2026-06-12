---
title: "cmus and cuefiles"
date: 2013-08-24
forum: Multimedia Software
---

### Post by shantiq on 2013-08-24
ok so i had a good look at moc   and now i am looking at cmus to see how they compare



cmus says it offers cuefile reading but so far i am failing to get that going  .... any of you know howto and could help here?   moc does not have that


installed from git [here]("https://github.com/cmus/cmus")


and it did not add cuefile by default  ,   reading around found i had to add ```
 sudo apt-get install libcue1 libcue-dev
```


now it shows all good in plugins

> cmus --pluginsInput Plugins: /usr/local/lib/cmus/ip
  mad:
    Priority: 55
    File Types: mp3 mp2
    MIME Types: audio/mpeg audio/x-mp3 audio/x-mpeg
  cue:
    Priority: 50
    File Types:
    MIME Types: application/x-cue






so i go to 5  find a cuefile which i have tested in audacious  [flac with flac]

and click a     then to to 2 [library]    and see nothing!


what am i missing?  any of you guys can help here 
    
thanx   shan

---

