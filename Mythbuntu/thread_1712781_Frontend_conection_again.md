---
title: "Frontend conection again"
date: 2011-03-23
forum: Mythbuntu
---

### Post by axelsvag on 2011-03-23
Yes I know there have been hundreds of threads about the problem connecting a remote frontend to the backend. But none of them I have read have solved my problem.
I have a perfectly working combined BE/FE running mythbuntu 10.04 with mythtv 0.24. 

I have installed a FE on a laptop with mythbuntu 10.10 mythtv 0.24. 

I have no problem accessing the combined BE/FE with the IPadress from the laptop with just the FE installed and I am able to get into the webinterface. But when I use the Frontend I do not get any access.

 I have checked the three mysql.txt files on the combined BE/FE and they say the same as the three mysql.txt on the separate FE with one exception. The first line at the combined BE/FE says localhost and on the FE it says the correct IP number, though I have changed the IPadress in the mythbackend setup to the real one for the machine.

 It feels that it is a very small problem to solve before everything is working as i suppose to, or?

---

### Post by thatguruguy on 2011-03-23
Are you asking a question?

---

### Post by axelsvag on 2011-03-24
Sorry. Yes I am asking a question.

Can someone give me an advice howto make my remote frontend connect to my master backend?

---

### Post by David Grigor on 2011-03-24
In mythbuntu controlcentre on the backedn under the mysql tab ther is a flag that needs to be checked if your allowing remote connections. Did you check that setting ? 

If I recall that is the only thing I needed to get my multiple remote Front ends to work ( other than localhost to IP setting you mentioned ).

---

### Post by axelsvag on 2011-03-24
I did not find that tab but I got it working after playing around. What made my remote frontend to connect was me changing the password. 

I had used the same password in the remote frontend as the frontend in the combined FE/BE. I just tried the password mythtv and all of a sudden everything worked. So the problem is solved but I have no idea why that password worked and why it should be different than the combined FE/BE.

---

