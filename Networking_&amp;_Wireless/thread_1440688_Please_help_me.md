---
title: "Please help me"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by Freddyg1912345 on 2010-03-27
So, I have been going through the forums a little bit and i cant find a solution to my problem. I recently installed Ubuntu 9.10 onto my Dell laptop, its an older model, not really sure what the exact name is; but anyway, when I logged on, there was not wireless connection, and after fumbling through some on-line tutorials, I feel I have gotten no farther. Does anyone know of a simple guide just to get me connected to the wireless connection (i believe mine is Ethernet)?? I don't think I have any trouble finding a wireless card or whatever, I am just really new to Ubuntu and I don't know where to start... any help would be good, 

Thanks

---

### Post by bkratz on 2010-03-27
> **Freddyg1912345 said:**
> So, I have been going through the forums a little bit and i cant find a solution to my problem. I recently installed Ubuntu 9.10 onto my Dell laptop, its an older model, not really sure what the exact name is; but anyway, when I logged on, there was not wireless connection, and after fumbling through some on-line tutorials, I feel I have gotten no farther. Does anyone know of a simple guide just to get me connected to the wireless connection (i believe mine is Ethernet)?? I don't think I have any trouble finding a wireless card or whatever, I am just really new to Ubuntu and I don't know where to start... any help would be good, 

Thanks




A good start would be to go to the terminal (Applications>>Accessories>>Terminal) and enter the following

```
lspci | grep Network
```

Copy/paste the output back here or simply report it back.

( that is a lowercase L in the beginning of that command not a 1)

---

### Post by Freddyg1912345 on 2010-03-28
> **bkratz said:**
> A good start would be to go to the terminal (Applications>>Accessories>>Terminal) and enter the following

```
lspci | grep Network
```Copy/paste the output back here or simply report it back.

( that is a lowercase L in the beginning of that command not a 1)
  
what does that bar in between the two commands mean?

---

### Post by bkratz on 2010-03-28
> **Freddyg1912345 said:**
> what does that bar in between the two commands mean?

The "bar" is called a pipe.  The following is the definition found it the Ubuntu Pocket guide.

 [http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)


Piping
Piping is similar to redirection except that it&#8217;s used to pass the output of
one command to another&#8212;rather like connecting a pipe between the
two commands, in fact!
The pipe symbol (|) is used for this purpose. On most keyboards this
symbol can be found by hitting Shift and backslash.
Taking the previous example, if we wanted to pipe the output of the ls
command into sort, to alphabeticize it, we would type the following:
&#61607; ls|sort 
A common use of piping is to pass the output of a command to the grep
command, which searches for a word or phrase. For example, if you
have a huge file listing containing hundreds of files/folders, and want to
find if report.doc is amongst them, you could type the following:
&#61607; ls|grep report.doc 
Incidentally, if you see no output, the search phrase wasn&#8217;t found.


The command will look at the pci bus and look for something with "network" in it, which will be the network controller and report back what it found.

---

