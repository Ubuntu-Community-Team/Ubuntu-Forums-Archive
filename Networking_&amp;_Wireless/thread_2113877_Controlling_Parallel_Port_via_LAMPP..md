---
title: "Controlling Parallel Port via LAMPP."
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by Prathmesh Halgekar on 2013-02-08
Hello, I am trying to control my parallel port through web. I have installed LAMPP as server.  For this i have written a c program which controls the parallel port which works completely fine when executed via terminal. And have aslo written a cgi file which calls the above c program in CGI-BIN in lampp. Above everything works fine when i execute the .cgi file  through terminal(I verified it as the program turns the LED to glow which is attached to my Parallel Port)....

BUT problem arises when i try to do the same through we server(lampp). I have a html file linked to a cgi file which inturn executes
  the c program for controlling the parallel port......whenever i click on
  button on the html form the cgi script gets called but the c program is not
  getting executed as the led attached to the parallel port does not glow or
  flicker.....i do login to the ubuntu system as root and i have given all
  permission to all file.(for eg chmod 755 filename). The above html program
  when call a cgi script it doesnt execute the c program. 

But when tried the
  same through terminal it works fine. Please help me to get through
  this problem.I would be really thankful to you.   Thank you.

---

