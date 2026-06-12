---
title: "Likewise Open autocomplete Terminal"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by RD1945 on 2010-09-07
Hi all,

I'm having a bit of a struggle here.
I recently installed likewise-open 6 to logon to my company domain.
All is working fine but one thing, the gnome-terminal autocomplete function.

All that the terminal shows is a "$" sign and nothing else.
When I type in a part of a word and press "TAB" it registers as a tab and does not show the autocomplete options that I normally have.

Can someone please help me with this because it's very annoying to type a long sentence every time.

Thanks in advance

---

### Post by RD1945 on 2010-10-06
Anyone??? I have tried to uncomment the autocomplete lines in /etc/bash.bashrc

---

### Post by haertie on 2010-10-10
I have the same problem, but no solution. Sorry

---

### Post by haertie on 2010-10-10
here the solution ;-)

source: [http://www.likewise.com/community/index.php/forums/viewthread/797/](http://www.likewise.com/community/index.php/forums/viewthread/797/)

"...
 Open terminal and notice that the command prompt only shows “$”.  Type 
  bash 
  This will give you the usual command prompt you expect. 
  To make this permanent, edit the likewise registry with the lwregshell utility.. 
  sudo /opt/likewise/bin/lwregshell 
   me@mymachine:~$ sudo /opt/likewise/bin/lwregshell 
  \> cd HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory 
  HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory> set_value AssumeDefaultDomain 1 
  HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory> set_value LoginShellTemplate /bin/bash 
  HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory> quit 
  Back at the command prompt clear the cache before restarting the machine. 
  sudo /opt/likewise/bin/lw-ad-cache --delete-all..."




bye ;-)

---

### Post by atworkwithjf on 2010-10-12
If you are using the verison of likewise-open in the apt-get repo I'd suggest you update to the version on the Likewise Open website.  It contains a number of fixes and improvements that I think will make your life easier.

Among the changes in 6.0 is a registry tool that will allow you to globally set the user's shell to bash which has file completion by default.  This way you will get this every login for every user.

You can get the new version of Likewise-Open at:

    [http://www.likewise.com/download/](http://www.likewise.com/download/)

Once you have it installed you'll find that it's installed in /opt/likewise (this is according to accepted standards, /opt is the correct install location for software that's not part of the distribution's standard repository).

To set all user's shell to bash:
```

    > sudo /opt/likewise/bin/lwconfig LoginShellTemplate /bin/bash

```
Another handy change is to have your machines assume your default domain so users can log in without prepending the domain in fromt of their user name:
```

    > sudo lwconfig AssumeDefaultDomain true 

```
Hope that helps,

-atworkwithjf

---

