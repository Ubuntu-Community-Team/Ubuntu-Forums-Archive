---
title: "Ekiga uses 100% CPU when using VOIP"
date: 2009-01-15
forum: Multimedia Software
---

### Post by svaens on 2009-01-15
Hi all, 

This is quite possibly a pulseaudio related problem, either Ekiga not supporting pulseaudio, or pulseaudio not doing something it should (I expect the first). 

When I do the sound test on Ekiga, when setting up, where you 'sound in' and it echos back to you what you said. It seems to work (although I don't know how reliably it will work) but it uses 100% CPU. The frame is even still responsive and all.... so it could possibly be not so very bad.. but i am scared off by this 100% CPU thing... .that I haven't bit the bullet and bought some credit with a SIP provider. 

I need something (desperately) to replace Skype. Never mind the fact that at the moment all those who I need to communicate with are on skype (that closed source b$%$%r) I will convert them!!! But can't do that until I find an alternative. 

The best alternative on Ubuntu seems to be, and should be, the default installed VOIP tool, Ekiga. But if that doesn't even work correctly on a fresh default installation of Hardy (the long term support version) then.... what is a guy to do!

Has anyone else noticed this kind of problem?

Has anyone else a better alternative?

Does anyone know if this problem is fixed in Intrepid?

Thanks and kind regards to all posters!


svaens

---

### Post by svaens on 2009-01-15
anyone?

---

### Post by Miguel on 2009-01-17
Hello!

I beforehand tell you that this post isn't very likely to resolve your issues. It's a possibility that you may be using one of the advanced codecs (unlikely if you are using the default 8.04 ekiga) and that could be too much for your CPU. What is your system? Are you using the webcam?

In any case, when you test the sound, are you sure that the culprit of the 100% CPU usage is Ekiga? You can check it in a terminal using the command **top** (exits with 'q') or by running the gnome-system-monitor. Also, there are a couple of numbers you can dial to check whether Ekiga is working fine or not.

Finally, a word of advice. Don't waste much energy trying to convert your friends to Ekiga. They are used to skype and its quirks. You may mention that you use an alternative, but I don't think you will be able to convert them to Ekiga unless they run Linux or a BSD.

---

### Post by svaens on 2009-01-18
Hi, and thanks for the reply.

I just now rechecked the exact behaviour of the application, and had a look at the process table using 'top' as you suggested. Please see below. 

I did a callback test using  Ekiga, at the address "sip:520@ekiga.net". 
It actually seemed to work quite well. 
While I was doing that I was watching the CPU. 
Right now, as i'm running firefox and a text editor, the processor seems to bounce around the 9% to 20% mark. 
As I was running Ekiga to make the test call, it was up around the 85% mark. 

While that is not the run away 100% that i described at first... it is still not perfect. Or ?? Maybe i expect to much?

I would like to hear your opinion, of what one 'could' expect such a program CPU usage 'should' or 'could' be. 

Non the less... my call back test was very encouraging. I used it for quite some time..... and didn't hear any stuttering, or glitches. 
Perhaps something else was wrong on the day I first set it up. 

Also, as you can see having a look at the process table, Pulseaudio is up there using a good amount. 


So, to wrap it up, I will not ask you silly questions here, or ask you to spend time and iterations on this forum trying to fix any problem that may or may not exist with my setup. I just ask one question;

Do you think that my setup (for use with Ekiga) should or could be better given the information that i've given here? 


```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6322 sean      20   0  102m  33m  19m S 49.7  1.7   0:47.52 ekiga              
 5849 sean       9 -11 31192 6880 3740 S 10.6  0.3   0:09.73 pulseaudio         
 5581 root      20   0 46320  34m 9232 S  8.0  1.7   0:33.58 Xorg               
 6150 sean      20   0  270m 124m  27m S  2.7  6.2   1:22.74 firefox            
 5874 sean      20   0 53324  26m  14m S  2.3  1.3   0:05.56 gnome-panel        
 5872 sean      20   0 18556   9m 7384 S  2.0  0.5   0:01.70 metacity           
 6332 sean      20   0 76704  20m  11m S  2.0  1.0   0:00.94 gnome-terminal     
 5876 sean      20   0 15288 2528 1680 S  1.3  0.1   0:01.76 gnome-screensav    
 6575 sean      20   0 36488  20m  10m S  1.3  1.0   0:01.96 gedit              
 4823 messageb  20   0  2832 1304  796 S  0.7  0.1   0:00.46 dbus-daemon        
 4960 root      20   0 29732  852  524 S  0.3  0.0   0:02.34 iked.real          
 5875 sean      20   0 83792  40m  18m S  0.3  2.0   0:02.67 nautilus           
    1 root      20   0  2844 1692  544 S  0.0  0.1   0:01.60 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0   


```

---

### Post by Miguel on 2009-01-18
Hello again,

As long as your CPU usage is below 100%, you won't be missing "frames", or that's what I think. I've done a test in my computer (Lenovo T400, with a 2.4 GHz P8600 dual core processor), and ekiga uses around 40% of one processor at 800 MHz. So the CPU usage seems to be high. I've also used Ekiga successfully in a 1.7GHz Centrino laptop (bought in 2004), so any machine newer than this should have no issues using Ekiga. I'd bet that Intel Atom processors can use Ekiga without issues.

So, in short, I think your computer should be OK. In case you want to test it, and as I'm interested in calling fixed phones using ekiga, don't be shy to phone me. My name is Miguel Martinez at Ekiga. I won't be up for more than half an hour, but you can try. Please note that I'm spanish, so my english accent won't be the best.

---

### Post by Miguel on 2009-01-18
By the way, I can have missed them, but what are your system specs?

---

### Post by svaens on 2009-01-18
Hi, 

System specs are toshiba Satellite, Intel 1.7GHz processor. Something along the lines of 5 years old by now i think.. i've stuck in 2 Gig memory since then though... and a nice new larger hard drive... but the processor is the same. 
But then, back then, it didn't take a fast computer to run skype or so. Just with all the pulse audio configuration problems on ubuntu recently.... I wondered... 

As for calling... ... I am shy.... ;)    but I'll have a go. I just have to see if i can work out how to find your SIP address from your name!

---

### Post by Miguel on 2009-01-18
SIP address is el.quark in case you need it. By the way, your system specs look perfectly fine to me.

EDIT: Just for the reference for future readers, the conversation seemed to go OK. I think we were both shy, but it's great to see Ekiga does work as supposed. So it's probably normal to have high CPU usage.

---

