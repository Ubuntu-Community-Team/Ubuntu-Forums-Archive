---
title: "Automatically Connect to NAS w/ login prompt"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by mpotoka on 2009-04-22
I am fairly new to Unbuntu but I am trying to get better with it so we can switch our entire school over to linux. I've figured out how to accomplish this task with our XP machines but I'm unsure of how to do so in Linux.
 
Basically on the XP machines I have this .bat file run automatically when the users log in.
 
@ECHO OFF
net use s: /delete
cls
Set /P variable=[Enter Username:]
Echo.
Echo "Logging onto Student Storage with Username :" %variable%
Echo.
net use s: [\\nas\%variable%]("file://\\nas\%variable%") * /P:No
Pause
@EXIT
 
The purpose is that we have 20 laptops avaiable that students use. I just added a NAS for them to be able to store their files on. This way whenver someone logs in to the computer (a generic login used for all students) they input their uname and password and it maps their nas folder to a local drive--making it very simple for the students.
 
How could I do something like this in Ubuntu 8.04 LTS so that I can still use just a generic login for ubuntu yet have a prompt automatically startup to get a username/password to mount their personal NAS folder?

---

