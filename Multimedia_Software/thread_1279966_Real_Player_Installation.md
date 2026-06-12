---
title: "Real Player Installation"
date: 2009-10-01
forum: Multimedia Software
---

### Post by neon100 on 2009-10-01
I downloaded real player in deb format from real.com/linux. But when i open the file, it open Package Installer and says ERROR: Cannot install 'lsb'

any solution?

---

### Post by sisco311 on 2009-10-01
Install it from the medibuntu repos:
[https://help.ubuntu.com/community/RealPlayerInstallationMethods#Install ''realplayer'' from the Repositories]("https://help.ubuntu.com/community/RealPlayerInstallationMethods#Install ''realplayer'' from the Repositories")

---

### Post by neon100 on 2009-10-02
thanks sisco311. but my connection went out during the execution of command. I re-executed it after i was online again. I reloaded the list in synaptic but still  it doesn;t show the real player entry there.

---

### Post by neon100 on 2009-10-02
even after checking all the relavant options i still cannot install real player. any suggestions?

---

### Post by pmlxuser on 2009-10-02
install using the .bin from their site. it works like magic. 
```

sudo chmod +x Real...bin
/.Real...bin

```


you will be flying soon

---

### Post by neon100 on 2009-10-02
When i ask such dumb question i fell like i have horns on my head...

this is my first time installing from .bin otherwise i keep  searching for .debs which i fell easier to install. Can you kindly explain how to install .bin file? step by step. this is what i've done till now

I've downloaded the RealPlayer11GOLD.bin to desktop. 
I opened Konsole and typed cd Desktop and then sudo chmod +x RealPlayer11GOLD.bin
Now when i typed /.RealPlayer11GOLD.bin it says No such file or directory

---

### Post by neon100 on 2009-10-02
ok ok i get it. it was ./file.bin and  not /.file.bin
sorry. I still feel the horns.

---

### Post by pmlxuser on 2009-10-02
ohh sorry the comand for installtion is\

```

./RealPlayer11Gold.bin

```

and not
```

/.RealPlayer11Gold.bin

```
as written by me typo error hope it helps...

---

### Post by pmlxuser on 2009-10-02
ohh sorry the comand for installtion is\

```

./RealPlayer11Gold.bin

```

and not
```

/.RealPlayer11Gold.bin

```
as written by me typo error hope it helps...

---

### Post by neon100 on 2009-10-02
i installed the real player but now when i run  it from Applications  menu it says

Could not launch Real Player 11
Failed to execute child process
"realplay" (No such fie or directory)

I installed real player in /home/jj/RealPlayer

its not working ! what do i do now?

---

