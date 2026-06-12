---
title: "DVD Duplication System"
date: 2012-02-14
forum: Multimedia Software
---

### Post by TFroehlich3 on 2012-02-14
Hello Everyone! :D
  I have a system that I built with 1 DVD-ROM drive and 6 DVD Burners in it. I am running Ubuntu 11.10 (64-bit) on this machine, and I am looking for a DVD/CD burning software that will write to those 6 drives at one time. I am using this machine at my recording studio. I am aware that I could just buy a "duplication controller" and have a standalone DVD Duplicator, but I do not want that. Is there a software that will allow me to do that?:confused: I do a lot of duplication of DVD's for a local church (of their youth group plays, retreats, and worship rock band) along with the normal CD duplication for local bands for them to sell to their fans when performing at local coffee shops.
 
I have use a Windows based program that does this, if it came down to it could I just use that with WINE so it would work in Ubuntu?
 
    Let me know if you know of a good software to use! :)
        Thanks in advance!!!

---

### Post by winh8r on 2012-02-14
you can use 

```
cdrdao
```

which will allow you to specify how many devices to write to and their locations.

to get cdrdao enter the following in the terminal


```
sudo apt-get install cdrdao
```


Once it is installed you can get full info by entering

```
man cdrdao
```


hope this is of some use to you

---

### Post by TFroehlich3 on 2012-02-14
> **winh8r said:**
> you can use 
 
```
cdrdao
```
 
which will allow you to specify how many devices to write to and their locations.
 
to get cdrdao enter the following in the terminal
 
 
```
sudo apt-get install cdrdao
```
 
 
Once it is installed you can get full info by entering
 
```
man cdrdao
```
 
 
hope this is of some use to you
 
 
Thank you! I will try this when I get back to the office! So when I do this, if I try to burn something and I don't have blank media in all the drives, will it give me an error? Or just burn to the drives with blank media within them?

---

### Post by winh8r on 2012-02-14
It will only burn data to the drives that you specify.

If there is no drive to burn to specified, it will return an error.

---

### Post by TFroehlich3 on 2012-02-14
> **winh8r said:**
> It will only burn data to the drives that you specify.
 
If there is no drive to burn to specified, it will return an error.
 
 
Right, what I was trying to say. If I specified 6 drives and only put blank media in 4 of the drives, would it burn those 4, or want me to put in 6 blank discs?

---

### Post by SAKeeler on 2012-02-14
Have a look [here]("http://www.techrepublic.com/blog/doityourself-it-guy/diy-burn-multiple-cds-at-a-time-on-the-cheap/112")

Creators write up is [here]("http://turbojet.sourceforge.net/")

---

### Post by winh8r on 2012-02-14
The above post by SAKeeler should answer all your questions as those developers have taken the basic cdrdao package and incorporated it into an easy to use GUI.

This should enable you to only write to selected drives using the graphical interface, with all the passing of parameters done behind the scenes.

Hope this thread takes you closer to where you need to be.



To SAKeeler, thanks for that post, I have always used the command line options for cdrdao when I have needed it but it is certainly a worthwhile tool which seems to be the base package for a lot of CD/DVD burning applications with GUIs

---

### Post by SAKeeler on 2012-02-14
No problem, google really is your friend, provided you know what to ask it.  took a few times to narrow down which utils to include in a search ;)

To the OP, I have not used the software in my post above.  YMMV.
but it looks stable enough for what you need.

GL

---

### Post by andrew.46 on 2012-04-09
> **winh8r said:**
> To SAKeeler, thanks for that post, I have always used the command line options for cdrdao when I have needed it but it is certainly a worthwhile tool which seems to be the base package for a lot of CD/DVD burning applications with GUIs

There is now a reasonable wiki page that demonstrates the basics:

cdrdao
[https://help.ubuntu.com/community/cdrdao](https://help.ubuntu.com/community/cdrdao)

---

