---
title: "Audacity won't open files?"
date: 2011-03-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by r-senior on 2011-03-12
Is anyone else finding that Audacity won't open any files?

---

### Post by mc4man on 2011-03-12
If you're using audacity w/ the global menu try returning menu to audacity.

For opening audacity from anywhere but cli just edit the .desktop

```
gksudo gedit  /usr/share/applications/audacity.desktop
```

Change the Exec=audacity line to this
```
Exec=env UBUNTU_MENUPROXY=0 audacity
```
save and retry
If you need to also include audacity from cli then a different method is used - ask

edit: because it worked here (returning menu), looked for bug, didn't find though I'm not great at finding dups, so filed new
[https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/733939](https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/733939)

---

### Post by r-senior on 2011-03-12
Thanks. Yes that sorts it from the Dash. How do I eliminate the global menu in the case when I right click on a WAV file and "Open with Audacity"?

I'm assuming I can enter your CLI solution in the Nautilus "Open With" dialog as a custom command for WAV?

---

### Post by mc4man on 2011-03-12
> . How do I eliminate the global menu in the case when I right click on a WAV file and "Open with Audacity"?
The desktop edit should also inc. opening a file from the r. click context.

> I'm assuming I can enter your CLI solution in the Nautilus "Open With" dialog as a custom command for WAV?

no ,no need
In the case of audacity don't think there is any reason to 'adjust' the binary, but will show anyway for info sake.

Will edit in from other machine that has audacity, always try to ck. things first.

If wishing to try this it's probably best to return the .desktop to the orig. Exec=audacity ( though not 100 % needed I would

Edit: to return menu to app thru the binary itself (though again probably there isn't much use in inc. a cli audacity

The first group of 4 commands should be entered as one in terminal,  
After returning audacity.desktop to orig.- 

```
sudo bash -c "cat > /usr/bin/audacity.helper" <<EOF
export UBUNTU_MENUPROXY=0 
exec  audacity.real "\$@"
EOF
```
```
sudo chmod 755 /usr/bin/audacity.helper
```
```
sudo mv /usr/bin/audacity{,.real} && \
sudo ln -sf audacity.helper /usr/bin/audacity

```

If audacity was to update (and not be fixed) then simply rerun the _last _code box, that will reset the 'diversion'

I only use this method for apps that I know I'll use from cli, otherwise the desktop edit is fine.

---

### Post by r-senior on 2011-03-12
Sorry ... it does work with a right-click. I just needed to restart Nautilus. Someone else might find the CLI solution useful but no rush for me.

Thanks again.

---

### Post by mc4man on 2011-03-12
> Someone else might find the CLI solution useful but no rush for me.
I think you'll be fine w/ the /desktop edit, - i'll leave the method anyway.

If the bug againt this is addressed I'll post back, though I find many apps where the menus are better in the gui.

If audacity updates it's likely you'll need to re-edit the .desktop

---

### Post by mc4man on 2011-03-12
current active bug on 
[https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/731451](https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/731451)

---

