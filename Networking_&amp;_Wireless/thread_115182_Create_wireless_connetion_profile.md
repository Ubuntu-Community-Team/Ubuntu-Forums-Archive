---
title: "Create wireless connetion profile"
date: 2006-01-10
forum: Networking &amp; Wireless
---

### Post by healychan on 2006-01-10
Hello all,

I would like to create two profile of wireless connection, 1 for my home and other for my school.

At the moment I do
```
sudo iwconfig wlan0 essid "home"
sudo ifup wlan0
```
to gain the ip from the DHCP server.

I know that I can either do it with System > Administration > Networking or I can write my own script.
I would both ways although I fancy doing it with a script.

I tried with the System > Administration > Networking but it doesn't work. Any advice??

Also when I write a script which contain "sudo", how can I pass the password as an argument?? Would it be something like this
```
#!/bin/bash

sudo iwconfig wlan0 essid "school"
echo $1

```

---

### Post by harisund on 2006-01-10
Hmm, I doubt if you could use sudo like that.. that isn't going to work ..

What you could do is disable sudo's password feature for the particular commands needed to get wireless working, such as the ifconfig, iwconfig and dhclient commands. 

A nice idea to automate the process would be to automatically scan all found networks (using iwlist wlan0 scan) and grep for the network you are searching for. 
So if you have a script named connect, you could simply execute connect and it automatically scans and decides whether you are at home or at school. Or you could pass the name of the essid as an argument instead.

---

### Post by healychan on 2006-01-10
> A nice idea to automate the process would be to automatically scan all found networks (using iwlist wlan0 scan) and grep for the network you are searching for.
Yes, your are right, I don't need to make two script. I was just focusing on the sudo things and forgot something very basic.

Thanks for your advice:p

---

### Post by healychan on 2006-01-10
[QUOTE=harisund]
What you could do is disable sudo's password feature for the particular commands needed to get wireless working, such as the ifconfig, iwconfig and dhclient commands. 
[/QUOTE]
Which file/s should I configure in order to disable sudo.

---

### Post by healychan on 2006-01-10
I just find something interesting from "man sudo".

I said that the -S flag can cause sudo to read password from stdin instead of terminal device.

Which means that my "echo" idea may work, although storing pwd as plain text is not a good idea.........:rolleyes:

---

### Post by harisund on 2006-01-10
```
sudo visudo
```
This will fire up your editor, which will have an open file. That is the file you need to edit. 

Read this just in case..
[http://www.linuxhomenetworking.com/linux-hn/addusers.htm](http://www.linuxhomenetworking.com/linux-hn/addusers.htm)

---

### Post by browneyedgirl65 on 2006-01-11
Am I missing something?  Multiple profiles can be set up in System->Administration->Networking using the Network settings dialog.  Click on location's arrow button, choose create location, give it a name, set up all the various different properties for it.  Repeat for each wireless (or even "wired") location you've got.

Don't tell me after all that profile setup Ubuntu won't automatically select which of work/play/home it's detecting?

I mean, *Windows* can do that, surely it's a piece of cake for any linux distro?

---

### Post by PMO6022 on 2006-01-11
[quote=harisund]What you could do is disable sudo's password feature for the particular commands needed to get wireless working, such as the ifconfig, iwconfig and dhclient commands.[/quote] Couldn't you just run your script with sudo to give yourself access to the networking commands contained in the script?

---

### Post by healychan on 2006-01-12
[QUOTE=PMO6022]Couldn't you just run your script with sudo to give yourself access to the networking commands contained in the script?[/QUOTE]
When we type sudo, it will prompt and ask for the pwd.
Therefore, "sudo myscript" must pass my pwd to "sudo" to continue process. That's why I need to change the "sudo" to accept my pwd form stdin instead of the terminal device.

I believe there are many ways of doing it but I can only think of using "echo" likes command at the moment.

Please let me know if you have any ideas. Thanks a lot:p

---

### Post by PMO6022 on 2006-01-12
I guess I don't really understand what you are trying to do then.  I thought that you wanted to have a script that that you would run in a terminal to autodetect which wireless network was available (home or school) and connect to the appropriate one.

I thought your problem was that the networking commands (iwlist, iwconfig, ifup, etc) required superuser rights to execute, so you are trying to find a way to pass your password to the script as it runs.  My suggestion was to run your script as root (or with sudo), because then any shell commands contained in the script should be exectued with those privileges.  Therefore, you would not need "sudo" within the script.

Please let me know if I have misunderstood your problem.

---

### Post by healychan on 2006-01-12
[QUOTE=PMO6022]I thought your problem was that the networking commands (iwlist, iwconfig, ifup, etc) required superuser rights to execute, so you are trying to find a way to pass your password to the script as it runs.  My suggestion was to run your script as root (or with sudo), because then any shell commands contained in the script should be exectued with those privileges.  Therefore, you would not need "sudo" within the script.[/QUOTE]
Of course I can run my script with root privileges using "sudo myscript", however, my concern is how the shell pass our password to sudo. I am also interested in many commands and would like to find out how they interact with the system.

---

### Post by healychan on 2006-01-12
Sorry, I clicked the submit button twice:rolleyes:

---

### Post by nickj6282 on 2006-01-12
I've been watching this thread. Does anyone have or know where to find an example script that will do this?

Thanks
-Nick

---

### Post by PMO6022 on 2006-01-13
[quote=healychan]...my concern is how the shell pass our password to sudo. I am also interested in many commands and would like to find out how they interact with the system.[/quote] 
Then I guess my only suggestion is to read up on bash and sudo.  Somewhere in the documentation must be a discussion of how the commands interact with the system.  Sorry I couldn't be more help.

---

### Post by rgmussel on 2006-04-18
[QUOTE=browneyedgirl65]Am I missing something?  Multiple profiles can be set up in System->Administration->Networking using the Network settings dialog.  Click on location's arrow button, choose create location, give it a name, set up all the various different properties for it.  Repeat for each wireless (or even "wired") location you've got.

Don't tell me after all that profile setup Ubuntu won't automatically select which of work/play/home it's detecting?

I mean, *Windows* can do that, surely it's a piece of cake for any linux distro?[/QUOTE]

Actually, if there is a linux solution to this problem, I have not found it. There is an interesting idea for a two-script solution here: [http://www.wolfteck.com/ifupdown/]("http://www.wolfteck.com/ifupdown/"), but I haven't gotten that to work on my laptop, but I've got a more complicated problem.

If someone has found a solution, please let me know.

BTW, it seems like Network-Manager 6 might do the trick, but I can't seem to get that set up in Ubuntu. When I tried last night, I killed the Kernel. OOOOOPPPS!:oops: The highest version of Network-Manager from Ubuntu is 4.

---

