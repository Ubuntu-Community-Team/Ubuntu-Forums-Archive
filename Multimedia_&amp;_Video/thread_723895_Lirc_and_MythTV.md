---
title: "Lirc and MythTV"
date: 2008-03-14
forum: Multimedia &amp; Video
---

### Post by medley on 2008-03-14
Hi gang

I'm having no success getting my Hauppauge remote to work with MythTV. It does work in the console when I run 'irw'; the correct buttons are detected. However there is no response from MythTV.

There are two lircrc files, one in /etc/lirc and the other in /home/.mythtv, and they both contain the same stuff. The one in .mythtv is owned my mythtv and the one in /etc/lirc is owned by root, although I've messed around with the ownership of each of them trying different things.

What do I have to do to get the buttons to be recognized by MythTV?

Thanks

---

### Post by medley on 2008-03-14
Anyone? I'm almost there; I just need to know how to get MythTV to respond.

---

### Post by ADK01 on 2008-03-14
make sure your .mythtv/lircrc look like

begin
    prog   = mythtv
    button = <button on remote>
    config = <key>
end

If youre using the SVN version and the above doesnt work, try 

begin
prog = irxevent
button = <button on remote>
config = Key <key> CurrentWindow
end
for the second one make sure irxevent is running
for all of them, replace <key> and <button on remote> with the appropriate buttons, <key> is the keyboard press you want to simulate, <button on remote> is the name of the detected button on the remote

---

### Post by medley on 2008-03-14
> **ADK01 said:**
> make sure your .mythtv/lircrc look like

begin
    prog   = mythtv
    button = <button on remote>
    config = <key>
end

If youre using the SVN version and the above doesnt work, try 

begin
prog = irxevent
button = <button on remote>
config = Key <key> CurrentWindow
end
for the second one make sure irxevent is running
for all of them, replace <key> and <button on remote> with the appropriate buttons, <key> is the keyboard press you want to simulate, <button on remote> is the name of the detected button on the remote

Thanks for your suggestions. However, my lircrc file does seem to be correct. As I mentioned, there are two, one in .mythtv and the other in /etc/lirc.

They both are the same:

begin
  prog = mythtv
  remote = Hauppauge_350
  button = Go
  repeat = 2
  config = I
end

begin
  prog = mythtv
  remote = Hauppauge_350
  button = Guide
  repeat = 2
  config = O
end
 <snip>

In the one in /etc/lirc I also added a duplicate set for irxevent in the same file:

<snip>
begin
  prog = irxevent
  remote = Hauppauge_350
  button = Go
  repeat = 2
  config = I
end

begin
  prog = irxevent
  remote = Hauppauge_350
  button = Guide
  repeat = 2
  config = O
end
<snip>

When I try to run irxevent from the console I get the following error:

phil@Vostro:~$ irxevent
" in /etc/lirc//lircrc:1 ignored
irxevent: bad file format, /etc/lirc//lircrc:2

The funny thing is that there are no quotes in the lircrc file. Any other suggestions?

---

### Post by ADK01 on 2008-03-15
Your Irxevent part should look like

config = Key <key> CurrentWindow

Try changing that and see if that helps, make a backup of your /etc/lirc/lircrc and try just:

begin
prog = irxevent
button = Guide
repeat = 2
config = Key O CurrentWindow
end

let me know how that works out, once again, make sure irxevent is running
also, do you have two remotes?
if not,  try omitting the "remote =" line

---

### Post by medley on 2008-03-16
> **ADK01 said:**
> Your Irxevent part should look like

config = Key <key> CurrentWindow

Try changing that and see if that helps, make a backup of your /etc/lirc/lircrc and try just:

begin
prog = irxevent
button = Guide
repeat = 2
config = Key O CurrentWindow
end

let me know how that works out, once again, make sure irxevent is running
also, do you have two remotes?
if not,  try omitting the "remote =" line

Thanks again for the suggestion, however I can't get irxevent to run. I end up with that error about the invalid file format for lircrc.

---

### Post by xpavement on 2008-03-17
Is the LIRC daemon running? If not:

cd /etc/init.d
sudo ./lirc start

I don't have an /etc/lirc/lircrc file, just using the ~.mythtv/lircrc one. Also, I don't have any "remote" lines in my lircrc file, so maybe copy your /etc/lirc/lircrc file somewhere else for a bit.

You said the buttons were being detected correctly, but make sure that the codes being output from irw match what's in /etc/lirc/lircd.conf for the button, just in case.

MythTV needs to be compiled with lirc support also, so I would make sure whatever you are using does have that support in it. I think there is some output about lirc when you start mythfrontend from a terminal session that may give you some clues as well.

---

### Post by carlosjf on 2008-04-10
irxevent: bad file format, /etc/lirc//lircrc:2

I fixed this by removing DOS newLines.

dos2unix /etc/lirc/lircrc

---

