---
title: "Boots into TTY mode (operating system present)"
date: 2023-06-26
forum: MINT
---

### Post by sports fan Matt on 2023-06-26
First of all hello!  Good to see everyone (it's been a while). :)  Second, I got a Chromebook that is acting funny, it only boots into tty mode and it's been so long I cannot remember how to get it back to recovery mode.  (It boots to BIOS but nothing else.  Can anyone help?

Matt

---

### Post by Rubi1200 on 2023-06-26
Hi Matt,

What Ubuntu version are you running?

At the TTY can you run this command and post the output here in code tags:
```
inxi -GS
```

Let's see if some of the information can help us figure out what is going on.

---

### Post by sports fan Matt on 2023-06-26
[QUOTE=sports fan Matt;14148401]First of all hello!  Good to see everyone (it's been a while). :)  Second, I got a Chromebook that is acting funny, it only boots into tty mode and it's been so long I cannot remember how to get it back to recovery mode.  Running uname -r produces
5.15.0.-75-generic so I assume the kernel is there it just won’t let me get into recovery mode to repair

Matt[/QUOTE

---

### Post by sports fan Matt on 2023-06-26
It’s a Linux mint vera. , graphics driver, I 915 until Hans will you LT and great graphics exhort with Weiland driver X mod setting, GL data unavailable in Consol try G something display. I couldn’t find a way to post a Screenshots, so I just typed it out.

---

### Post by QIII on 2023-06-26
Moved to MINT.

---

### Post by oldfred on 2023-06-26
Moved to Mint sub-directory since not Ubuntu. QIII types faster. 
We are not sure what all the changes Mint does, even though based on Ubuntu.

If UEFI boot, you should be able to press escape key, just after vendor logo but before grub menu would normally appear to get grub menu.
Then can you boot recovery mode & its menu?

If you are booting to terminal, then it is a gui type issue. Did you make any changes? Normally Intel video just works, so did something related to graphics get updated? Do not know Mint's graphics.

---

### Post by sports fan Matt on 2023-06-26
The only packages I’ve removed war language packages that I did not need.

---

### Post by Rubi1200 on 2023-06-26
> [COLOR=#000000]If UEFI boot, you should be able to press escape key, just after vendor logo but before grub menu would normally appear to get grub menu.[/COLOR]
[COLOR=#000000]Then can you boot recovery mode & its menu?[/COLOR]

Did you try oldfred's suggestion from above?

---

### Post by sports fan Matt on 2023-06-26
I did and still went to tty sadly.

---

### Post by Rubi1200 on 2023-06-26
And what happens if at the TTY you try running these commands:
```
sudo apt update && sudo apt upgrade
```

Are there errors?

---

### Post by sports fan Matt on 2023-06-26
I can see the grub menu but it’s bypassing it. I’m now currently sitting at a GNU grub version 2.06. 
Grub>

---

### Post by sports fan Matt on 2023-06-26
There we go got into recovery. I will post back and see if it works.

---

### Post by sports fan Matt on 2023-06-26
I assume I want recovery mode, correct?

---

### Post by Rubi1200 on 2023-06-26
Yes. Correct.

---

### Post by sports fan Matt on 2023-06-26
So it appears I have no free space left on my device. How can I fix this to restore some space to possibly free one of these issues

---

### Post by Rubi1200 on 2023-06-26
If you select Clean in recovery mode and press Enter a terminal window should appear with options to free space up. That would be my first attempt.

---

### Post by sports fan Matt on 2023-06-26
The package lists or status file cannot be parse or opened.

---

### Post by sports fan Matt on 2023-06-26
E: wrote error saving space cache. I tried that suggestion and that’s what popped up.

---

### Post by Rubi1200 on 2023-06-26
I would also try the dpkg option in Recovery mode and see if that helps fix/clean any issues. You will need to select network before using dpkg to make sure you are connected.

---

### Post by sports fan Matt on 2023-06-26
running apt update gives a black flashing cursor

---

### Post by sports fan Matt on 2023-06-26
Nothing to clean in Dpkg

---

### Post by Rubi1200 on 2023-06-26
It might be best to use a liveUSB to boot and then see if you can access the drive and clean that way by removing things you know you do not need/want.

First backing up any important data of course.

---

### Post by sports fan Matt on 2023-06-26
That’s kind of what I was thinking. It might be time for a clean install. I have absolutely no idea what happened or why it got borked

---

### Post by sports fan Matt on 2023-06-26
Reinstalling from fresh ~ let's see how it works

---

### Post by sports fan Matt on 2023-06-26
This has solved the issue

---

### Post by Rubi1200 on 2023-06-26
Glad to hear you got things sorted out.

Please mark the thread Solved using the Thread Tools at the top of the first post.

---

