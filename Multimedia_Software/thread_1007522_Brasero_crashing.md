---
title: "Brasero crashing"
date: 2008-12-10
forum: Multimedia Software
---

### Post by Dumbestcrayon on 2008-12-10
Brasero locks up and crashes.

Heres the only error I got when I started it in terminal (I don't know if its relevant) 

I/O warning : failed to load external entity "/home/brett/.config/brasero/brasero.session"
Segmentation fault
brett@Brett:~$ "

The Segmentation fault comes when it closes on its own.

I click "Audio Project" then when I try and select the media to burn it locks up and I have to CTRL+C to close it in terminal.

I tried to apt-get remove and reinstall it but that didn't help.


Any ideas?

---

### Post by Eddie Wilson on 2008-12-10
I have not been able to get Brasero to operate properly in the last two versions of Ubuntu. Instead I installed Gnomebaker and have no problems at all. It seems that the package managers refuse to believe there is anything wrong with Brasero, but there is and its an app that won't even copy an audio cd.

---

### Post by Dumbestcrayon on 2008-12-10
Yeah I just installed Gnomebaker and it worked fine. I'm just gonna remove brasero since it crashes already.


Thanks.

---

### Post by Dumbestcrayon on 2008-12-10
Now I'm getting the same error when I try to add files in Gnomebaker.

Segmentation fault

Can anybody tell me what this means?

---

### Post by Trist on 2008-12-12
Hi,
I think I've had the same problem. When you select the mp3 files to burn Brasero lock's up. All I did was uncheck preview in View and it's worked fine since.

---

### Post by Dumbestcrayon on 2008-12-12
> **Trist said:**
> Hi,
I think I've had the same problem. When you select the mp3 files to burn Brasero lock's up. All I did was uncheck preview in View and it's worked fine since.

I just tried it and it didn't lock up. I didn't burn anything because I don't have anything to burn right now but I'll try it next time I do.

Thanks.

---

### Post by binbash on 2008-12-12
upgrade your brasero here : [http://www.getdeb.net/app/Brasero](http://www.getdeb.net/app/Brasero)

and try again.

---

### Post by PTo on 2008-12-14
It worked for me to! How nice that sometimes the solution is so incredibly simple... :D

---

### Post by Dumbestcrayon on 2008-12-14
Thanks a bunch. Like PTo said. Its always something simple.

---

### Post by Eddie Wilson on 2008-12-15
> **binbash said:**
> upgrade your brasero here : [http://www.getdeb.net/app/Brasero](http://www.getdeb.net/app/Brasero)

and try again.

Will that also take care of the audio cd copying problem?

---

### Post by Dumbestcrayon on 2008-12-24
> **Eddie Wilson said:**
> Will that also take care of the audio cd copying problem?

Im not having any issues with it so I assume it fixed it.

Give us more details on it and maybe we can help you.

---

