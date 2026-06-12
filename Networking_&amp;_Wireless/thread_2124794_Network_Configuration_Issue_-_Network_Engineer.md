---
title: "Network Configuration Issue - Network Engineer"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by Roobir on 2013-03-12
Hi kind folks!

I have been adventuring around linux platforms for a while now, but recently (as of steam's support on linux) completely moved my laptop and desktop at home over to linux. Now, even my laptop at work I moved over to linux. 

I apologise if this offends anyone, but I moved my work laptop over to Debian, namely the Crunchbang distro. It simply works amazingly on it, as I normally have quite a few hundred things open on it and the work laptop is not as powerful as the ones at home running Ubuntu.

Anyways, I am having a particular problem with pasting some of my router configurations over a telnet session. E.g. I want to paste the following:

!
!
policy-map DSL_XXXXXXXX_XXXX
!
 class class-default
  shape average XXXXX XXXXX XXXX XXXX
  bandwidth XXXXXXXXX XXXXXXX XXXXXX
  queue-limit XXXX XXXXX
!
!

This configuration is stored in a template saved in Microsoft Excel. I have a lot of these templates that are issued on Microsoft Excel. The problem comes in when I try to paste something from these templates, then it creates the word 'B' where there are sometimes up to three spaces between the values.

This was never a problem in Windows, using Putty. I tried installing Putty on Crunchbang and it still didn't want to work as it correctly does in Windows. I think it could be something to do with Ritch Text Font conversion.. perhaps!

Has anyone run into similar type of problems? I really want to stick with linux for all my office work, but this could mean I have to change back to Windows.

Oh, this happens on Ubuntu from my house as well. :/

Any help will be amazing gentlemen!

Kind regards,
Roob

---

### Post by Roobir on 2013-03-12
Might be something to do with ASCII and UTF8 perhaps?

---

### Post by Roobir on 2013-03-14
A bump for help! :)

---

### Post by steeldriver on 2013-03-14
I'm having a hard time understanding what this means
> **Roobir said:**
>  it creates the word 'B' where there are sometimes up to three spaces between the values
What application are you opening the excel files with, and how are you copying and pasting into the telnet session? Maybe it is bringing over some special / non-printing characters from the excel sheet? Sometimes it helps to paste into a plain text editor to remove any formating then immediately re-copy out of that.

---

### Post by Roobir on 2013-03-18
> **steeldriver said:**
> I'm having a hard time understanding what this means

What application are you opening the excel files with, and how are you copying and pasting into the telnet session? Maybe it is bringing over some special / non-printing characters from the excel sheet? Sometimes it helps to paste into a plain text editor to remove any formating then immediately re-copy out of that.

I was using LibreOffice to open Microsoft Office Excel spreadsheets. I tried copying it to Geany and changing it from UTF-8 to ASCII, but to no success. It only works if I copy it to an editor and manually remove the multiple spaces, was just wondering if there could be an easier way to do this, as there are quite a hefty amount of lines of code in the templates.

Thanks for the response!

---

