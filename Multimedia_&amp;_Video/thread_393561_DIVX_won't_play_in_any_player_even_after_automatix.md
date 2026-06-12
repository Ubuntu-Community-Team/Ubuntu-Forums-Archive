---
title: "DIVX won't play in any player even after automatix codecs install"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by konungursvia on 2007-03-25
I've tried for days. Does anyone know the names of the packages required to play divx movies, and can you answer the question, does the codec let me play them in principle with any or all my video players? And most importantly, can anyone give a brief step-by-step that will work? Also dvds dont mount or play in linux yet, is this related?

---

### Post by jackrobinson on 2007-03-26
> **konungursvia said:**
> I've tried for days. Does anyone know the names of the packages required to play divx movies, and can you answer the question, does the codec let me play them in principle with any or all my video players? And most importantly, can anyone give a brief step-by-step that will work? Also dvds dont mount or play in linux yet, is this related?

install **AUD-DVD codec**s from automatix (if you havent done that already)

---

### Post by konungursvia on 2007-03-26
Thanks, already tried that, and Automatix broke my aptitude list, and the divx still don't play. Any other ideas anyone?

---

### Post by jackrobinson on 2007-03-26
> **konungursvia said:**
> Thanks, already tried that, and Automatix broke my aptitude list, and the divx still don't play. Any other ideas anyone?
broke your "aptitude list"? what you  probably mean is it added the correct official ubuntu repos to your broken sources.list
ok it seems the divx codecs are in the "multimedia codecs" option on automatix. make sure thats installed.

---

### Post by konungursvia on 2007-03-26
Hi, no I had the correct official sources for almost all well known repos on my sources.list, but after running automatix, it broke aptitude's register of what was installed and suggested I run "sudo aptitude install -f" to fix it, which in turn suggested I uninstall a hundred and seventy-two programs, which I said no to. So automatix broke something.

---

### Post by jackrobinson on 2007-03-26
> **konungursvia said:**
> Hi, no I had the correct official sources for almost all well known repos on my sources.list, but after running automatix, it broke aptitude's register of what was installed and suggested I run "sudo aptitude install -f" to fix it, which in turn suggested I uninstall a hundred and seventy-two programs, which I said no to. So automatix broke something.
I am a 110% sure that your "well known" repos stand for **broken 3rd party repositories**. Don't add them.. They will only result in a ton of breakages. The errors that you saw was because of conflicts in apt (automatix acts partly as a wrapper for apt).. so it was not automatix at fault.. but your adding so many repositories with untested and broken packages.

---

### Post by konungursvia on 2007-03-27
I'm 10% sure you're overstating your confidence, but thanks for educating me. Which ones should be in there for Dapper?

---

### Post by jackrobinson on 2007-03-27
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main 
```

---

### Post by konungursvia on 2007-03-27
Trust you and have made my sources.list exactly like this. Thanks.

---

