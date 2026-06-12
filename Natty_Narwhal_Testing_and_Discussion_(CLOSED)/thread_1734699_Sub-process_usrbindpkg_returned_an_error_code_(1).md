---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2011-04-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Neo40 on 2011-04-20
I'm using 11.04 beta2 and after upgraded packages I got this error:
```
eric@eric-Desktop:~$ sudo apt-get upgrade 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
2 partiellement installés ou enlevés.
Après cette opération, 0 o d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n]*? 
Paramétrage de apport (1.20.1-0ubuntu3) ...
start: Job failed to start
invoke-rc.d: initscript apport, action "start" failed.
dpkg*: erreur de traitement de apport (--configure)*:
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 1
dpkg*: des problèmes de dépendances empêchent la configuration de apport-gtk*:
 apport-gtk dépend de apport (>= 0.41)*; cependant*:
 Le paquet apport n'est pas encore configuré.
dpkg*: erreur de traitement de apport-gtk (--configure)*:
 problèmes de dépendances - laissé non configuré
Aucun rapport «*apport*» n'a été créé car le message d'erreur indique une erreur consécutive à un échec précédent.
                                                                                                                  Des erreurs ont été rencontrées pendant l'exécution*:
 apport
 apport-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)
eric@eric-Desktop:~$ 
```

Any idea?
Thanks

Edit: Problem solved with latest update! :)

---

### Post by PaulW2U on 2011-04-20
I wouldn't worry too much, it'll be sorted out on one of the next updates. I got a similar error but apport-kde was mentioned in the error message as I'm using Kubuntu 11.04.

---

### Post by 5149.5 on 2011-04-20
It looks like there is a bug in the post installation script. I tried purging and reinstalling. I guess the devs got tired of all those pesky bug reports. :P

---

### Post by wizard10000 on 2011-04-20
Yup.  apport's broken in both 32- and 64-bit.  I tried purging and reinstalling - no joy.

---

### Post by pauljwells on 2011-04-20
It is a known bug and a fix has been written. It's in build right now and will be on the mirrors in a few hours.

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/767498]("https://bugs.launchpad.net/ubuntu/+source/apport/+bug/767498")

---

### Post by 5149.5 on 2011-04-20
This doesn't look quite right: 

if [ "`dd if=/proc/sys/kernel/core_pattern count=1 bs=1 2>/dev/null`" != "|" ]
then
        exit 1

---

### Post by theanswriz42 on 2011-04-20
It's all happy now.

---

### Post by ursoouindio on 2011-04-21
I'm still getting it.

Natty Beta 32-bit.

---

### Post by wizard10000 on 2011-04-21
> **theanswriz42 said:**
> It's all happy now.

My 64-bit installation isn't.  apport installed but refused to start.

---

### Post by jahLux on 2011-04-21
> **wizard10000 said:**
> My 64-bit installation isn't.  apport installed but refused to start.

Same here - Fedora 15 looms larger and more lovely each passing day  . . . . . !!

---

### Post by wizard10000 on 2011-04-21
> **jahLux said:**
> Same here - Fedora 15 looms larger and more lovely each passing day  . . . . . !!

Found the problem and fixed it.  See post #53 in the bug report -

[https://bugs.launchpad.net/apport/+bug/767498](https://bugs.launchpad.net/apport/+bug/767498)

But to paraphrase, /etc/default/apport has 'enabled=0' in there.  Change it to 1 and then

```
sudo start apport
```

and you should be golden.

I don't know why a purge didn't remove that file.  Strange.

---

