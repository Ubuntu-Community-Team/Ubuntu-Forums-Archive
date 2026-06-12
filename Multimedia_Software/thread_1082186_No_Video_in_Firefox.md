---
title: "No Video in Firefox"
date: 2009-02-27
forum: Multimedia Software
---

### Post by alligoodw on 2009-02-27
I've installed Ubuntu 8.10 on a HP Pavilion dv6000.  I've corrected the nVidia problem as well as the wireless problem.  Now it's time to correct a problem with Firefox.

When I go to Nasa.gov, CNN.com and Fancast.com, no video plays.  As a matter of fact, Firefox freezes altogether.  Bottom line - all pages which require video doesn't currently work.  What one addon is necessary to get things running?  I know there has to be a simple solution to this problem.  To be perfectly honest with you, I'm a little surprised that this isn't automatically set-up during the Ubuntu 8.10 installation.

---

### Post by Therion on 2009-02-27
Start by Copying and Pasting the following into a Terminal:

```
sudo apt-get install ubuntu-restricted-extras flashplugin-nonfree
```

Enter your password when prompted and answer yes to the prompts, legal-ese.

---

