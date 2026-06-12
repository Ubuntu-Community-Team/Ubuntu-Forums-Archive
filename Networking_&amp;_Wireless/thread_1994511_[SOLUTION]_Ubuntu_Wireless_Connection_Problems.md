---
title: "[SOLUTION] Ubuntu Wireless Connection Problems"
date: 2012-06-02
forum: Networking &amp; Wireless
---

### Post by PugnaciousPhlebotomist on 2012-06-02
Greetings UbuntuForums.org!
This is my first post, and in fact, I signed up only to make this post after finding a solution to a problem that I have been having for a while. I am here to (try to) help, so forgive me if these solutions have been posted or the formatting is wrong.
This may work on Ubuntu variants, but I have only tested it on 12.04 Precise Pangolin.

Disclaimer: I cannot guarantee that these will work, proceed at your own risk. I am no expert when it comes to Linux, and there is no promise that nothing bad will happen to your system. You have been warned.



Possible Solution One: Search *Additional Drivers* in the Dash Home, and click the result. From there, choose a driver and click activate. [This won't likely have a wireless driver, but is a possible solution.]
[IMG]http://bit.ly/Ml5YHM[/IMG]



Possible Solution Two: In the terminal [Ctrl+Alt+T or search* Terminal* in Dash Home], run
*sudo rfkill unblock all*
[IMG]http://bit.ly/KBaxuQ[/IMG]
This usually removes the soft block, and you can check by using command
[I]rfkill list all



[/I]Possible Solution Three: In the terminal [see step two], use the command
[I]sudo apt-get update
[/I]Put in your password, and once this process is completed, use
*sudo apt-get upgrade*
The *update* command updates repositories, and the *upgrade *command installs new packages. This may take a few minutes. After completed, restart the computer.
More about the *apt-get *command, [click here.]("https://help.ubuntu.com/8.04/serverguide/apt-get.html")



 Possible Solution Four: If your wireless network is disabled by *A Hardware Switch* according to Ubuntu, but the wireless button itself doesn't seem to be doing anything, this is a possible solution. When turning on the computer, press the wireless button (or switch) *once* on your computer *between *the BIOS screen and the actual boot menu (where you choose your operating system or the default OS actually starts) on startup. 



Possible Solution Five: Reset BIOS. When turning on your computer, look for a message concerning boot options or BIOS. Press that key and open the BIOS from there. In the BIOS, load defaults usually by pressing F9 and then confirming your changes.
 [IMG]http://bit.ly/L4W3QT[/IMG]







Hopefully, one of these steps will help you with your problem. Step 5 solved my issue. If there are any changes I should make, or any new ideas, reply/message me and I will add it and give you credit. Good luck, and I hope this post helps!

---

### Post by Paddy Landau on 2012-06-03
Thank you for sharing your discoveries.

By the way, here is how to [mark a thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

