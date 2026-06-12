---
title: "While trying to install ACL, messed up my partition, cannot load Ubuntu anymore"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by AfrikaDietmar on 2010-06-09
Hi Ubuntu tribe,

currently i'm working hard on setting a small network amongst 4 computers. In this network i want to give different permission to these shared folders. I've managed to share folders through Samba GUI. Thats good so far, only they are not password protected.

After some reasearch i found that I should create some linux users, and then apply these as new samba users. Then install ACL (Access Control List).

I found a tutorial that was for Ubuntu 9.0x that explained how to do it,and i tried to use the same steps on 10.04. 

There was a step where it says todo the following:

```
sudo nano /etc/fstab
```Then change in the partition the word 

```
relatime.erro$
``` into ```
relatime.acl$
```But in my partition there wasn't this, there was [COLOR=Red]**errors=remoun$**[/COLOR]

I changed it not knowing the [COLOR=Red]risk [/COLOR]i'm taking, wondering that i might work...

Anyway, when i restarted my computer, it cannot mount my partition anymore, i access /etc/fstab but i don't have write permission to correct this. I also tried to login is sudo su but this didn't help.

Any idea how i can fix this ? Or must i reinstall ubuntu from scratch...

---

### Post by AfrikaDietmar on 2010-06-09
Hi Jakman,

i don't think that this is a solution to my problem. I know my password, i just don't have writing permission on:


sudo nano /etc/fstab
so i cannot undo what i changed for my ext4 partition.

If i cannot get write permission or if there is another way to solve this, i'm afraid i will need to do a reinstall ? hmm... I prefer to wait, because it will take a lot of time to reconfigure everything again. Maybe someone has an idea...

---

### Post by Sunspire on 2010-06-09
A friend of mine gave me this solution.

when booting press arrow key down before the splash screen appears

this will display the grub menu

press e

select the line that says "kernel"
then press e again

you will be able to modify the line

go to the end of the line

add the word "single" with no quotes at the end of the line

press ENTER
then press b

This will boot your machine into the command line

then type nano /etc/fstab and revert your changes

I hope this helps

---

### Post by AfrikaDietmar on 2010-06-09
ok, i gave it a try.

When my computer boots, i see the grub menu.

I went on Ubuntu, with Linux 2.6.32-22-generic and pressed e there.

A page opens, but i don't see anywhere the word "Kernel", all the details that i see can be edited.

So thats where i'm stuck again...

---

### Post by Sunspire on 2010-06-09
Here is what I was trying to explain

[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

---

### Post by AfrikaDietmar on 2010-06-09
The problem is that for me, it says record fail and i cannot select the kernel as described.
I can see it, but not select it with e. 
So i don't know how to get into edit grub mode - i guess it doesn't work.

> **Procedure: Boot Linux Grub Boot Loader into single user mode**

 (1) At grub boot screen (after restart)
 (2) Select  the kernel


---

### Post by AfrikaDietmar on 2010-06-09
I used the cd to boot from cd ubuntu, i was able to have a look at /etc/fstab but couldn't make any changes as i don't have the permissions... hmm...

---

### Post by Paddy Landau on 2010-06-10
Let's find out about your permissions and take it further.

[LIST=1]
[*]Boot from your Live CD.
[*]Click on Places, and find your hard drive (somewhere below 'Computer'). Open (click) it.
[*]Open (double-click) the [FONT=Courier New]etc[/FONT] folder.
[*]Find [FONT=Courier New]fstab[/FONT], right-click and select Copy.
[/LIST]
Now open a terminal.

Type '[FONT=Courier New]ls -l [/FONT]' (without the quotes), then right-click and Paste. It will look like this:
[FONT=Courier New]ls -l file:///media/*linux*/etc/fstab[/FONT]
with some different name for *[FONT=Courier New]linux[/FONT]*.

Use your left- and right-arrow keys and your Delete or Backspace keys to delete [FONT=Courier New]file://[/FONT] so that it looks like the following (again with a different name for *[FONT=Courier New]linux[/FONT]*):
[FONT=Courier New]ls -l /media/*linux*/etc/fstab[/FONT]

Press Enter. It should look something like this:
[FONT=Courier New]-rw-r--r-- 1 root root 761 2010-05-10 14:06 /media/*linux*/etc/fstab[/FONT]

Post the results here.

(BTW, as a newcomer to Linux, you'll probably find that [FONT=Courier New]sudo nano *filename*[/FONT] is not as easy as [FONT=Courier New]gksu gedit *filename*[/FONT].)

---

### Post by Paddy Landau on 2010-06-10
> **AfrikaDietmar said:**
> [COLOR=Red]**errors=remoun$**[/COLOR]...
There's a problem with a newcomer using nano.

There is no $ in the file; that's nano's way of showing that there's more in the line.

Next time, as I mentioned in the previous post, use
[FONT=Courier New]gksu gedit /etc/fstab[/FONT]

Also, I notice with unease that fstab in Lucid no longer has relatime in it. I will do some investigation about this. In your case, simply add acl to your line. So, if your line looks like this:
```
UUID=14f19230-9284-4ee6-943f-70a82712e9ea / ext4 errors=remount-ro 0 1
```then add acl as follows:
```
UUID=14f19230-9284-4ee6-943f-70a82712e9ea / ext4 acl,errors=remount-ro 0 1
```I recommend adding relatime, too:
```
UUID=14f19230-9284-4ee6-943f-70a82712e9ea / ext4 acl,relatime,errors=remount-ro 0 1
```If you're just testing Ubuntu, and you have nothing valuable saved on it, then you may want to consider simply reinstalling Ubuntu and starting again.

---

### Post by AfrikaDietmar on 2010-06-10
Hello,

> Post the results here.the result is: 

```
ubuntu@ubuntu:~$ ls -l /media/21c80cef-5ed3-498d-92b9-9c0118e18739/etc/fstab 
-rw-r--r-- 1 root root 829 2010-06-08 19:59 /media/21c80cef-5ed3-498d-92b9-9c0118e18739/etc/fstab

```I can't access gksu because i don't have editing rights.

> If you're just testing Ubuntu, and you have nothing valuable saved on  it, then you may want to consider simply reinstalling Ubuntu and  starting again.Will the procedure for me to have editing rights be more complex and timely than a reinstall ?
If i can have editing rights and correct my fstab, i think everything should be back to normal.

---

### Post by Paddy Landau on 2010-06-10
> **AfrikaDietmar said:**
> I can't access gksu because i don't have editing rights.
That doesn't make sense. gksu simply tells Linux that you want to run a GUI program as root. gksu will ask for your password (except from the Live CD) and then attempt to run the program that you requested.

Thanks for posting your output. It looks perfectly satisfactory.

So, what I want you to do now is this. Post the contents of that fstab. A good way would be:

[LIST=1]
[*]Repeat steps 1-4 from [post 8]("http://ubuntuforums.org/showthread.php?p=9439207#post9439207") to get your fstab again.
[*]Press Alt-F2.
[*]Type [FONT=Courier New]gedit *Ctrl-V*[/FONT]. This should result in the following:
[FONT=Courier New]gedit /media/21c80cef-5ed3-498d-92b9-9c0118e18739/etc/fstab
[/FONT]If not, then manually amend it.
[*]Click *Run*.
[*]Now you'll see your fstab. Highlight everything (by pressing Ctrl-A), and copy (by pressing Ctrl-C).
[*]Open a browser, come to this thread, and paste the contents here.
[/LIST]

---

### Post by AfrikaDietmar on 2010-06-10
problem solved.

I didn't get the logic first that i should have done the following:

[FONT=Courier New]gksu gedit [/FONT]/media/21c80cef-5ed3-498d-92b9-9c0118e18739/etc/fstab 
Then i had writing rights, i didn't realise that i was actually trying to change the fstab on the cd itself. 

Once i updated the fstab with the details you mentioned, afterwards i was able to boot again without any problems.

Thanks a lot for your help! :)

---

### Post by Paddy Landau on 2010-06-10
Fantastic.

Please remember to mark the thread as solved.

---

