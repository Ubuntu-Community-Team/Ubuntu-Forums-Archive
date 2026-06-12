---
title: "Auto-Mount User's Windows Share"
date: 2012-01-25
forum: Networking &amp; Wireless
---

### Post by JonLarson3 on 2012-01-25
Hello,

We are running an Edubuntu LTSP server inside my school. We have it set up to boot anywhere in the school, authenticate through the Windows Active Directory for the Student Accounts, etc. All we have left to do is automatically mount the Students drive upon login. Each student has their own drive. We created a script that seems to work, but it requires sudo which we don't want to give access to for the students. This is the script I have:

```

/bin/mount -t cifs -o username=$USER //backup.prairiefarm.k12.wi.us/students/$USER /home/likewise-open/PRAIRIEFARM/$USER/Desktop/$USER\ on\ backup

```When you execute it, it requires user to be root. Is there a way to not require root, or is there a better method to mounting the drives.

Any help would be great!

---

