---
title: "Cannot copy files from Rhythmbox to iPod"
date: 2009-12-17
forum: Multimedia Software
---

### Post by porlaizquierda on 2009-12-17
With another distribution of Linux i was able to plug in my ipod, copy the songs that were in my rhythmbox library and paste them into my ipod. now i am back with ubuntu 9.04, and when i try to copy and paste a sing i get the message: 

Error transferring track

Error creating directory: Permission denied

can anyone help me on this one?

---

### Post by loboc on 2009-12-18
an ipod library may be missing


or it may be a permission error try adding your self to the group disk

```

sudo useradd disk yourname

```

---

### Post by porlaizquierda on 2009-12-18
i did that command, but i got this:

Options:
  -b, --base-dir BASE_DIR       base directory for the new user account
                                home directory
  -c, --comment COMMENT         set the GECOS field for the new user account
  -d, --home-dir HOME_DIR       home directory for the new user account
  -D, --defaults                print or save modified default useradd
                                configuration
  -e, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
  -f, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -g, --gid GROUP               force use GROUP for the new user account
  -G, --groups GROUPS           list of supplementary groups for the new
                                user account
  -h, --help                    display this help message and exit
  -k, --skel SKEL_DIR           specify an alternative skel directory
  -K, --key KEY=VALUE           overrides /etc/login.defs defaults
  -l,                           do not add the user to the lastlog and
                                faillog databases
  -m, --create-home             create home directory for the new user
                                account
  -N, --no-user-group           do not create a group with the same name as
                                the user
  -o, --non-unique              allow create user with duplicate
                                (non-unique) UID
  -p, --password PASSWORD       use encrypted password for the new user
                                account
  -r, --system                  create a system account
  -s, --shell SHELL             the login shell for the new user account
  -u, --uid UID                 force use the UID for the new user account
  -U, --user-group              create a group with the same name as the user


so what does that mean? i still cannot copy mp3s from rhythmbox to my ipod.

---

### Post by bkmfs on 2009-12-18
----

---

### Post by porlaizquierda on 2009-12-18
i found hipo ipod management tool. it doesn't play music, but it very simply imports music onto your ipod. still a bit of a disappointment though because i like rhythmbox a lot and have never had this happen before. i still don't know how to go around the permissions.

---

### Post by Extract_Here on 2009-12-18
I use banshee it works really nice. i didnt have any problems.

---

### Post by porlaizquierda on 2009-12-21
just an FYI. don't use hipo! it erased all my music on my ipod!

---

