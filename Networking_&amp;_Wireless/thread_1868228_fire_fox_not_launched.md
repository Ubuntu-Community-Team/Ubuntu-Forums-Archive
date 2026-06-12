---
title: "fire fox not launched?"
date: 2011-10-24
forum: Networking &amp; Wireless
---

### Post by Matrix01 on 2011-10-24
recently, I installed 11.04,
connected wifi,
clicked firefox icon on task bar.
it did not start.

---

### Post by scania_gti on 2011-10-24
Run firefox from terminal too see whats happened.

---

### Post by theluli on 2011-10-24
hi

l have the same problem , when l am trying to open firefox , always is saying that 

"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system"

l have to restart pc , than i open once , after l clos , and l am trying to open again , l am getting the same message 

anyone has idea what might be the problem

---

### Post by Matrix01 on 2011-10-25
i get exactly same message,

did u use unetbootin and iso file when u installed 11.04?
that's how i did.

---

### Post by theluli on 2011-10-25
No , l have installed from DVD , and in the beginning there was no problem , since 2 days this problem appeared 

l installed opera since l need a browser , but l might admit that there is nothing like firefox 

anybody there that can help us
fiuuuuuuuuuu fiuuuuuuuuuuuuu SOS

---

### Post by lovinglinux on 2011-10-25
Use this command or enter System Monitor and kill firefox-bin.

```
killall firefox-bin
```

---

### Post by Matrix01 on 2011-10-26
i am new to buntu.
what is terminal?

> **scania_gti said:**
> Run firefox from terminal too see whats happened.

---

### Post by Matrix01 on 2011-10-26
how can i enter this command?
and 
what is system monitor? 

> **lovinglinux said:**
> Use this command or enter System Monitor and kill firefox-bin.

```
killall firefox-bin
```

---

### Post by scania_gti on 2011-10-26
[Terminal - is there]("http://www.psychocats.net/ubuntu/terminal").
For launch firefox, just type in terminal: ```
firefox
```
Thats all. Terminal will print any errors, then copy text and paste here.
Or try Lovinglinux answer - type ```
killall firefox-bin
```
Or find "system monitor" - this look like windows "task manager".

---

### Post by Matrix01 on 2011-10-27
i did it, 
thank u.
typed firefox in terminal, and launched F-fox.

---

### Post by Matrix01 on 2011-10-27
here's screen shot of terminal.
can u read this and find any errors?

[ATTACH]205580[/ATTACH]

---

### Post by Matrix01 on 2011-10-27
and here's copy of system monitor;
'firefox sleeping.'
what does this mean?
I am writing thisnthread, and FF is sleeping?
[ATTACH]205582[/ATTACH]

---

### Post by Matrix01 on 2011-10-27
how do u find lovinglinux answer?

---

### Post by lovinglinux on 2011-10-27
> **Matrix01 said:**
> here's screen shot of terminal.
can u read this and find any errors?

[ATTACH]205580[/ATTACH]

That is an error with the global menu. If you still experience issues starting Firefox from the launcher and the command* killall firefox-bin* doesn't solve the problem, then try to disable the global menu. Type *about:addons* in Firefox address bar, then click the Extensions selector, if not already selected, find *Global Menu Bar integration*, click the button to disable it and restart.

> **Matrix01 said:**
> and here's copy of system monitor;
'firefox sleeping.'
what does this mean?
I am writing thisnthread, and FF is sleeping?
[ATTACH]205582[/ATTACH]

Noting to worry about. The application is just not doing or processing anything at the moment. You might also find some  *zombies* processes. Although the name is scary, it is also nothing to worry about. See [http://askubuntu.com/questions/48624/what-are-zombie-processes](http://askubuntu.com/questions/48624/what-are-zombie-processes)

---

### Post by theluli on 2011-10-27
thanks lovinglinux

now its working , can you explain a little bit more what was the problem ?

---

### Post by theluli on 2011-10-27
Sorry l did not see the last post 

regards

---

### Post by lovinglinux on 2011-10-27
> **theluli said:**
> Sorry l did not see the last post 

regards

You are welcome.

---

### Post by Matrix01 on 2011-10-28
typed killall firefox in terminal, and here's screen shot;
[ATTACH]205651[/ATTACH]

---

### Post by Matrix01 on 2011-10-28
killall firefox did not work.
so
disabled global menu bar integration in extension,
and 
worked.
thank u,

---

### Post by lovinglinux on 2011-10-28
> **Matrix01 said:**
> killall firefox did not work.
so
disabled global menu bar integration in extension,
and 
worked.
thank u,

You are welcome. BTW, the command is actually *killall firefox-bin*. Sorry for that.

---

### Post by Matrix01 on 2011-10-30
firefox does not launch again.
same problems recurring after shut PC down

global menu bar integration is disabled,
and
killall firefox-bin does not work neither.

[ATTACH]205857[/ATTACH]

[ATTACH]205865[/ATTACH]

---

### Post by lovinglinux on 2011-10-30
Try a clean profile.

---

### Post by Matrix01 on 2011-10-30
> **lovinglinux said:**
> Try a clean profile.

does existing FF have to be removed before installing new one?

---

### Post by lovinglinux on 2011-10-31
> **Matrix01 said:**
> does existing FF have to be removed before installing new one?

No. But sometimes when you upgrade the user profile get corrupted.

---

### Post by Matrix01 on 2011-11-04
[ATTACH]206276[/ATTACH]
check this out.
Is this FF 4.0?

---

### Post by lovinglinux on 2011-11-04
> **Matrix01 said:**
> [ATTACH]206276[/ATTACH]
check this out.
Is this FF 4.0?

Yes. You need to upgrade your applications, because Firefox version is 7 now and will be 8 in a couple of days. You can do that through Update Manager.

---

### Post by Matrix01 on 2011-11-06
11.04 had gone through updating, but message "update failed" showed up.
FF is updated to 7.0, but it does not show up on monitor when i clicked FF icon in launcher.

> **lovinglinux said:**
> Yes. You need to upgrade your applications, because Firefox version is 7 now and will be 8 in a couple of days. You can do that through Update Manager.

---

### Post by wobert on 2012-12-01
Hello all,

I have some long time not been able to use firefox,

killing it from process manager is the only option, through the terminal I was unable

Please refer to the attached file , it prompts partially, graphically does not show the full window it is prompting, seems like an update, then get stuck completely

next steps to help me solve this issue?

thanks

---

