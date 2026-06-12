---
title: "What user do you install mythbuntu as?"
date: 2009-09-02
forum: Mythbuntu
---

### Post by Levander on 2009-09-02
Got to reinstall Mythbuntu this week.

It seems like the user you create during the install process is the user myth-frontend runs under (because that is the user gdm auto-logins, I guess). 

I've been using the user-name I always use on all my computers.  But, it just seems weird running mythtv as me because I'm far from the only one who uses it.  So, what name should I use?

All the backend stuff has permissions set up for user, "mythtv", so I don't want to use that.  Just to keep permissions from the front-end and the back-end separate.

I guess I could use "mythf", but that sounds cryptic.  Just calling the user "myth", there's no mnemonic to remember which user is for the front-end and which is for the back-end.

Anybody gotta good name?

Are there any real advantages of making up another user name?  Other than just being OCD about it?

---

### Post by tgm4883 on 2009-09-02
> **Levander said:**
> Got to reinstall Mythbuntu this week.

It seems like the user you create during the install process is the user myth-frontend runs under (because that is the user gdm auto-logins, I guess). 

I've been using the user-name I always use on all my computers.  But, it just seems weird running mythtv as me because I'm far from the only one who uses it.  So, what name should I use?

All the backend stuff has permissions set up for user, "mythtv", so I don't want to use that.  Just to keep permissions from the front-end and the back-end separate.

I guess I could use "mythf", but that sounds cryptic.  Just calling the user "myth", there's no mnemonic to remember which user is for the front-end and which is for the back-end.

Anybody gotta good name?

Are there any real advantages of making up another user name?  Other than just being OCD about it?

Don't use mythtv. I use my regular user name. Makes it a lot easier if I need to ssh in for some maintenance

---

### Post by Levander on 2009-09-02
> **tgm4883 said:**
> Don't use mythtv. I use my regular user name. Makes it a lot easier if I need to ssh in for some maintenance

Yeah, probably.  You do it as your regular user name, and you don't have to put a user name in on the ssh command line.  Maybe that is the only thought to be put behind what username to use to run mythfrontend under?

I wasn't going to use "mythtv".  If you read the post, I was thinking about using something like "mythf".  The "f" on the end being for front.

---

### Post by SiHa on 2009-09-03
FWIW, my BE/FE is called 'mythbox', and the remote frontend is imaginatively called 'frontend'. Easy to remember you'd think, except when I needed to ssh into the backend server, a month after I'd first set it up, I spent about an hour wondering why I couldn't log into 'backend':redface:

---

### Post by movieman on 2009-09-03
Just create a new user with limited privileges: mine, oddly, is called 'mythbuntu'. That way you can also configure that account specifically for mythtv and not have to screw up your own user account: on my system, for example, that account just runs myth frontend with no window manager when it logs in.

---

### Post by williammanda on 2009-09-06
I agree with most of the posts. Just use a simple generic name so that all can use the system without having to remember some cryptic user name.
Thanks

---

