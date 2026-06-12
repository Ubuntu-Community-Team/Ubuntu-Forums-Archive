---
title: "Remove MythTV backend leaving the front end"
date: 2011-03-02
forum: Mythbuntu
---

### Post by peterhocking on 2011-03-02
Hi everyone

I recently setup my 2nd MythTV frontend, but for some reason it failed to install the themes. A bit of googling suggested that I should run "sudo apt-get install mythtv mythtv-themes" which I ran & it installed all the missing themes plus MythTV backend & the MySQL server.

Can anyone suggest how to remove the backend & MySQL server setup but leave the themes? If this can't be done, how can I disable the backend & MySQL server?

TIA

Peter

---

### Post by tgm4883 on 2011-03-02
> **peterhocking said:**
> Hi everyone

I recently setup my 2nd MythTV frontend, but for some reason it failed to install the themes. A bit of googling suggested that I should run "sudo apt-get install mythtv mythtv-themes" which I ran & it installed all the missing themes plus MythTV backend & the MySQL server.

Can anyone suggest how to remove the backend & MySQL server setup but leave the themes? If this can't be done, how can I disable the backend & MySQL server?

TIA

Peter

apt-get remove mythtv-backend mysql

You didn't need to install the mythtv package

---

### Post by peterhocking on 2011-03-03
> **tgm4883 said:**
> apt-get remove mythtv-backend mysql

You didn't need to install the mythtv package

Many thanks, if only I had looked a bit closer when I installed the themes :(

Thanks for your help,

Peter

---

