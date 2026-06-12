---
title: "vim in mutt"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by aneez004 on 2012-05-23
I have installed mutt.Its having nano editor.Can anyone tell how to change the editor to vim

---

### Post by eleftg on 2012-05-23
add this line to your ~/.bashrc

```
export EDITOR=vim
```

then enter this command:

```
source ~/.bashrc
```

and your mutt editor is changed

Alternatively you can add this line to your .muttrc

```
set editor='vim'
```

---

### Post by aneez004 on 2012-05-23
> **eleftg said:**
> add this line to your ~/.bashrc

```
export EDITOR=vim
```

then enter this command:

```
source ~/.bashrc
```

and your mutt editor is changed

Alternatively you can add this line to your .muttrc

```
set editor='vim'
```
Thanks for your reply
Adding to .bashrc file is not working;the editor is still nano

Where is the .muttrc file? there is /etc/Muttrc file

---

### Post by eleftg on 2012-05-23
copying from [http://www.mutt.org/doc/manual/manual-3.html](http://www.mutt.org/doc/manual/manual-3.html)

While the default configuration (or preferences) make Mutt usable right out of the box, it is often desirable to tailor Mutt to suit your own tastes. When Mutt is first invoked, it will attempt to read the system configuration file (defaults set by your local system administrator), unless the -n command line option is specified. This file is typically /usr/local/share/mutt/Muttrc or /etc/Muttrc. Mutt will next look for a file named .muttrc in your home directory. If this file does not exist and your home directory has a subdirectory named .mutt, mutt try to load a file named .mutt/muttrc.

.muttrc is the file where you will usually place your commands to configure Mutt.

---

### Post by matt_symes on 2012-05-23
Hi

Is an issue with your alternatives ?

From the terminal, please post the output of 

```
update-alternatives --get-selections | grep editor
```

If it points to nano then type

```
sudo update-alternatives --config editor
```

Point the editor symlink to vim.

Kind regards

---

### Post by aneez004 on 2012-05-23
> **matt_symes said:**
> Hi

Is an issue with your alternatives ?

From the terminal, please post the output of 

```
update-alternatives --get-selections | grep editor
```

If it points to nano then type

```
sudo update-alternatives --config editor
```

Point the editor symlink to vim.

Kind regards
editor                         auto     /bin/nano
gnome-text-editor              auto     /usr/bin/gedit

---

### Post by aneez004 on 2012-05-23
> **eleftg said:**
> copying from [http://www.mutt.org/doc/manual/manual-3.html](http://www.mutt.org/doc/manual/manual-3.html)

While the default configuration (or preferences) make Mutt usable right out of the box, it is often desirable to tailor Mutt to suit your own tastes. When Mutt is first invoked, it will attempt to read the system configuration file (defaults set by your local system administrator), unless the -n command line option is specified. This file is typically /usr/local/share/mutt/Muttrc or /etc/Muttrc. Mutt will next look for a file named .muttrc in your home directory. If this file does not exist and your home directory has a subdirectory named .mutt, mutt try to load a file named .mutt/muttrc.

.muttrc is the file where you will usually place your commands to configure Mutt.
yo it works!!
vim /etc/Muttrc
    set editor='vim'


Thanks boss

---

### Post by matt_symes on 2012-05-23
Hi

> **aneez004 said:**
> editor                         auto     /bin/nano
gnome-text-editor              auto     /usr/bin/gedit

Your editor is pointing to nano. You can change it to point to vim if you want as i posted above by changing its config.

```
sudo update-alternatives --config editor
```

This will be a global change though but if vim is your prefered editor then this is not a problem.

**EDIT:** I see you already found another solution. It's a good solution but will only apply to mutt. For a global solution (such as visudo pointing to vim as well) then update the alternatives symlink.

Kind regards

---

### Post by aneez004 on 2012-05-23
> **matt_symes said:**
> Hi



Your editor is pointing to nano. You can change it to point to vim if you want as i posted above by changing its config.

```
sudo update-alternatives --config editor
```

This will be a global change though but if vim is your prefered editor then this is not a problem.

**EDIT:** I see you already found another solution. It's a good solution but will only apply to mutt. For a global solution (such as visudo pointing to vim as well) then update the alternatives symlink.

Kind regards
yes it works too
Thanks boss ...
Now vim is my default editor

---

