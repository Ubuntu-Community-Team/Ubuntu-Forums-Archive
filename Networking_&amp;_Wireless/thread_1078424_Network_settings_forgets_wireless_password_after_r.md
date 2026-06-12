---
title: "Network settings forgets wireless password after restart  *8.04*"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by henryf61 on 2009-02-23
The title says it all. I have a dual boot laptop with 8.04 and XP and restart often so this is becoming a nuisance. I read a similar thread about a week ago for 8.10 and nothing there helped. 

Background: My laptop was new in November, 2007 and came with 7.10 installed. 8.04 was just installed this month. It took a fresh install rather than an upgrade because my system was missing a few critical files for the upgrade. I never had to re-enter the network password before 8.04. I have a Linksys router and use Firefox 3.0.6 and Thunderbird 2.0.0.19.

Any help will be appreciated. TIA.

Henry

---

### Post by Iowan on 2009-02-23
Verify that the pertinent information is in */etc/network/interfaces*.

---

### Post by henryf61 on 2009-02-23
Iowan,

Thanks for the tip but it didn't work for me. Maybe I don't know how to follow the directions. I went to the howto link. There they said the problem was in /etc/netprobe.d and I should create a file bad_list with a one line command. I did all this but when I tried to save the file, I got the message "You do not have the necessary permission . . ." I did this from a terminal command line after typing "sudo l" and the sudo command said I have permission for *all* commands. That exhausts my limited knowledge and I am still at square one.

Henry

---

### Post by Iowan on 2009-02-23
> **henryf61 said:**
>  I got the message "You do not have the necessary permission . . ."  Sounds like a "sudo" problem.  What command(s) did you issue from the terminal?  It should be something like **sudo nano filename** or **gksudo gedit filename** (using the name for your file bad_list instead of "filename").

---

### Post by henryf61 on 2009-02-23
I am making some progress. At a terminal, I wrote

cd /etc/modprobe.d
gksudo gedit bad_list

I then pasted in this line

alias net-pf-10 off

which is what the instructions in your link said to do. I saved the file successfully and restarted but my system still forget the network password. I had to re-enter it in Network Settings before getting to the internet.

Possibly the command I pasted into bad_list wasn't quite the right one for my situation??  I don't understand the command.

Thanks for your help so far.
Henry

---

