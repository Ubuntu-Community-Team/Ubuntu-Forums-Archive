---
title: "Problems faced using Ubuntu 9.10(karmic koala)"
date: 2009-11-29
forum: Multimedia Software
---

### Post by Scholar1987 on 2009-11-29
I face the following problems using Ubuntu 9.10

Hi

I have just upgraded my OS from Ubuntu 9.04 to Ubuntu 9.10, but I am facing these problems...

1. I get this error message when I login
 
                  Could not update .ICEauthority file /home/scholar./.ICE authority

2. I get this dialogue block when I start Mozilla firefox 3.6

   **   Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full    ** 
    
                       & moreover this::the search engines (one beside ) the navigator,  in mozilla(3.6 namaroka) aren't working..if I give any text in it, It didnt even load any page and no action is performed.


3. I am using WINE to access some of the files of windows....example I am trying to access Ultrasurf.exe, but no  action is performed....
 
       Can anyone help me out to fix them:D

---

### Post by whoop on 2009-11-29
> **Scholar1987 said:**
> I face the following problems using Ubuntu 9.10

Hi

I have just upgraded my OS from Ubuntu 9.04 to Ubuntu 9.10, but I am facing these problems...

1. I get this error message when I login
 
                  Could not update .ICEauthority file /home/scholar./.ICE authority

2. I get this dialogue block when I start Mozilla firefox 3.6

   **   Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full    ** 
    
                       & moreover this::the search engines (one beside ) the navigator,  in mozilla(3.6 namaroka) aren't working..if I give any text in it, It didnt even load any page and no action is performed.


3. I am using WINE to access some of the files of windows....example I am trying to access Ultrasurf.exe, but no  action is performed....
 
       Can anyone help me out to fix them:D

Looks like your permissions are messed up.. Try:
```

sudo bash
chown -R <yourusername>:<yourusername> /home/<yourusername>
chmod 644 /home/<yourusername>/.dmrc
chmod 644 /home/<yourusername>/.ICEauthority
exit

```

Replacing <yourusername> with your username....

---

### Post by Scholar1987 on 2009-11-29
Hey thanks for replying but I am getting this problem
**my username is scholar**
if I have given this statement 
root@scholar:~# chown -R scholar:scholar /home/scholar
this is returned
chown: cannot access `/home/school/.gvfs': Permission denied
and  no problems with the following...
root@niket:~# chown 644 /home/niket/ .dmrc
root@niket:~# chown 644 /home/niket/ .ICEauthority

[B]if I give chown scholar:scholar / home/scholar no message is delivered but 

when I reboot the system again gives: Could not update ICE authority
[/B]

---

### Post by whoop on 2009-11-29
> **Scholar1987 said:**
> Hey thanks for replying but I am getting this problem
**my username is scholar**
if I have given this statement 
root@scholar:~# chown -R scholar:scholar /home/scholar
this is returned
chown: cannot access `/home/school/.gvfs': Permission denied
and  no problems with the following...
root@niket:~# chown 644 /home/niket/ .dmrc
root@niket:~# chown 644 /home/niket/ .ICEauthority

[B]if I give chown scholar:scholar / home/scholar no message is delivered but 

when I reboot the system again gives: Could not update ICE authority
[/B]

I'm not sure but I think the permission denied on .gvfs is not a problem
You are supposed to chmod the .dmrc and .ICEauthority file, not chown them (in these two cases)...

furthermore, you are talking about having a user name "scholar", yet you are accessing a home folder named /home/niket and getting a error message containing /home/school/. This is confusing to me. Could just be some typo's in your post, but be sure to enter correct information when you are messing about in the command line, especially when in super user mode.

---

### Post by Scholar1987 on 2009-11-29
Hey I replace with chmod for .drmc and . ICE authority.. but the problem still persists
 
I still get this problem cannot update ICE authority after login
 
Nw I think my system is totally messed up...[COLOR=red]after the ICE authority error I get these[/COLOR]
[COLOR=red][/COLOR] 
[SIZE=2]**1. There is a problem with configuration server(usr/lib/libgconf2-4/gconf-semity-check-2 exited with status 256)**.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]**2. Nautulus could not create the following required  folders /home/scholar/Desktop/ home/scholar/.nautilus**[/SIZE]
 
      [COLOR=navy]before running nautilus,a please create these folders or set permissions such that nautilues can create them[/COLOR]
[SIZE=2][/SIZE] 
[SIZE=2][COLOR=black]**after this**[/COLOR] [/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2][COLOR=darkslategray]the desktop doesnot loads and an yellow screen gets without any icon or panel and after reboot also the same continues....[/COLOR][/SIZE]
[SIZE=2][COLOR=#2f4f4f][/COLOR][/SIZE] 
[SIZE=2][COLOR=#2f4f4f]I had upgraded directly from ubuntu 9.04 to 9.10..I think the problems I face is  due to upgradition without using CD...[/COLOR][/SIZE]
 
[SIZE=2][COLOR=#2f4f4f]Please try to fix this problem...I have important content in my system...[/COLOR][/SIZE]
[SIZE=2][COLOR=#2f4f4f][/COLOR][/SIZE] 
[SIZE=2][COLOR=#2f4f4f]Can I reinstall Ubuntu 9.10 onto 9.10 without missing my files and contents[/COLOR][/SIZE]

---

### Post by whoop on 2009-11-29
> **Scholar1987 said:**
> Hey I replace with chmod for .drmc and . ICE authority.. but the problem still persists
 
I still get this problem cannot update ICE authority after login
 
Nw I think my system is totally messed up...[COLOR=red]after the ICE authority error I get these[/COLOR]
[COLOR=red][/COLOR] 
[SIZE=2]**1. There is a problem with configuration server(usr/lib/libgconf2-4/gconf-semity-check-2 exited with status 256)**.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]**2. Nautulus could not create the following required  folders /home/scholar/Desktop/ home/scholar/.nautilus**[/SIZE]
 
      [COLOR=navy]before running nautilus,a please create these folders or set permissions such that nautilues can create them[/COLOR]
[SIZE=2][/SIZE] 
[SIZE=2][COLOR=black]**after this**[/COLOR] [/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2][COLOR=darkslategray]the desktop doesnot loads and an yellow screen gets without any icon or panel and after reboot also the same continues....[/COLOR][/SIZE]
[SIZE=2][COLOR=#2f4f4f][/COLOR][/SIZE] 
[SIZE=2][COLOR=#2f4f4f]I had upgraded directly from ubuntu 9.04 to 9.10..I think the problems I face is  due to upgradition without using CD...[/COLOR][/SIZE]
 
[SIZE=2][COLOR=#2f4f4f]Please try to fix this problem...I have important content in my system...[/COLOR][/SIZE]
[SIZE=2][COLOR=#2f4f4f][/COLOR][/SIZE] 
[SIZE=2][COLOR=#2f4f4f]Can I reinstall Ubuntu 9.10 onto 9.10 without missing my files and contents[/COLOR][/SIZE]

Looks like the scholar account is corrupted/incomplete. Do you have any other accounts on the system (niket perhaps) ?

---

### Post by Scholar1987 on 2009-11-30
No, I dont have any other user in my system...
 
Can't we fix it

---

