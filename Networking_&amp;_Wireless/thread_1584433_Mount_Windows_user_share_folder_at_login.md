---
title: "Mount Windows user share folder at login"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by guimenez on 2010-09-29
i need to always mount the user share of my Windows server at Ubuntu login. 

Can anyone help me on this please? 

This is my server struture: 

Server 
|-Group1 
| |-user1 
| 
|-Group2 
| |-user2 


i’ve found that i need to configure pam mount and i have this example: 

<volume user="user" fstype="smbfs" server="krueger" path="public" 
mountpoint="/home/user/krueger" > 

but i don’t know what to change relative to my server folder struture. 


many thanks

---

