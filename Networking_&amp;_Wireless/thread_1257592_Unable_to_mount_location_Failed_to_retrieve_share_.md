---
title: "Unable to mount location Failed to retrieve share list"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by dancil on 2009-09-04
Hi, I have been trying all the suggestions in the forums but nothing has worked!

Ubuntu Intrepid Ibex and Jaunty - Same problem
I can see all the workgroups and the domain but can not access the shares.

In desperation I copied the smb.conf file from a Sabayon installation, which by the way works perfetcly, to the Ubuntu Intrepid machine and it still does not work. It seems therefore that it is not the smb.conf causing the problem.

Can somebody please help.

---

### Post by Boneyard on 2009-09-04
I am having exactly the same problem and nothing i seem to do works!

I have found a workaround that sort of solves my problem in the short term it might help you too, I am a TOTAL novice so there is no code involved :D 

OK got to:

Applications > Add/Remove

Make sure that in the 'Show' box it says 'All available applications'

In the 'Search' box type 'smb4k'

Install the SMB4k package.

Goto Applications > Accessories > smb4k

When the window opens, there are 3 tabs at the bottom, click the first one 'Network Neighbourhood' then click the workgroup that you want to open, it will 'hopefully' list all the computers in your network, along with their ip adresses. 

Remember the IP of the computer you want to look at, 

go to Places > Network

when the window opens, click the little icon on the left that looks like a pencil and paper, it will show you an address bar

in the address bar type 'smb://the IP you remembered <---- obviously dont type this, type in the ip address, it will be somthing like 192.168.1.1 or somthing 

there you go! it should work!

If not then... Im stuck!

Sorry its a long winded thing, but as i said i am a total novice, and trying to give up windows! there is probably a better way and i have no doubt other more competent users will laugh but this worked for me until i find a reason why my samba wont work too!!

Good luck!

---

### Post by dancil on 2009-09-07
Thank you.

I'll try this and report back.

---

### Post by dancil on 2009-09-08
Thanks Boneyard,

I can access the shares this way but it is a workaround and would like to use Samba as in for example Sabayon. Hopefully this will be fixed in a later version of Ububntu.

---

