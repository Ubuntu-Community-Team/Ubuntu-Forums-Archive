---
title: "Are there any voice manipulation software available for Ubuntu?"
date: 2010-08-18
forum: Multimedia Software
---

### Post by Scood on 2010-08-18
I have done numerous searches on several search engines and have come up with nothing, I run Ubuntu 10.04. Thank you in advance for taking the time to answer this question.

---

### Post by cchhrriiss121212 on 2010-08-18
It helps if you explain what you want to achieve. Do you want real time effects or post processing?

---

### Post by Scood on 2010-08-18
Yes i would like it to edit input from a microphone in realtime.

---

### Post by texaswriter on 2010-08-18
Helpful hints: Be more specific... be as specific as you can. Specificaly say what you are using this for [in as many details as possible].

---

### Post by Scood on 2010-08-19
well ok, im looking for voice manipulation software, a voice changer, a voice morpher, a piece of software that can, in real time, alter input from a microphone so that it sounds different than the original input the output should be easily manipulated. It would be nice if it simulated a virtual microphone to record and/or but mostly and, use for prank calls.

---

### Post by texaswriter on 2010-08-19
There is a distro of Ubuntu called Ubuntu Studio

This is a list of pertinent software, by no means comprehensive. Some of what you named is somewhere on the list. I'll leave it to you or others to go into more details. 

[https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)

---

### Post by cchhrriiss121212 on 2010-08-20
Studio is good for making music, but you should be able to just use Audacity. Enable as many effects as you like and check the software playthrough box in the preferences menu.

---

### Post by Scood on 2010-08-20
i have tried audacity, it does not edit input in real time, instead you record it then you add effects to it, not very effective in a conversation.

---

### Post by madmax.santana on 2010-08-20
If you know a little bit of MATLAB & C, you would be able to create such a widget yourself and then link it to a C/C++ program (make a simple GUI using Glade)... But in the end, you are not going to be able to have conversation using that software because you will need to be able to port the output of the program to the VoIP application or whatever you are using to make the call... But I suppose that will need some initiative and a lot of effort.

Also, prank calls might be fun, but they are immoral after all.

AFAIK, there is no such software in Ubuntu or even for Windows which can accomplish voice masking + transferring the masked output to some other program at once. Maybe I am wrong, but I read somewhere that it requires a lot of system memory. Of course, it is possible if the software that you are using to make the conversation offers such a feature itself. It rules out the "porting output" problem.

---

### Post by Stigmata13 on 2010-08-20
> **madmax.santana said:**
> If you know a little bit of MATLAB & C, you would be able to create such a widget yourself and then link it to a C/C++ program (make a simple GUI using Glade)... But in the end, you are not going to be able to have conversation using that software because you will need to be able to port the output of the program to the VoIP application or whatever you are using to make the call... But I suppose that will need some initiative and a lot of effort.

Also, prank calls might be fun, but they are immoral after all.

AFAIK, there is no such software in Ubuntu or even for Windows which can accomplish voice masking + transferring the masked output to some other program at once. Maybe I am wrong, but I read somewhere that it requires a lot of system memory. Of course, it is possible if the software that you are using to make the conversation offers such a feature itself. It rules out the "porting output" problem.
Actually there are a few programs for windows, one of which I can remember off the top of my head being Screamingbee I believe, It's done by using a specific driver for input and can be used over voip/chatrooms etc., but as for linux I'd be surprised if there was such a program.

---

### Post by cchhrriiss121212 on 2010-08-20
> **Scood said:**
> i have tried audacity, it does not edit input in real time, instead you record it then you add effects to it, not very effective in a conversation.
My apologies, I thought Audacity could do that. Try out installing jackd and calf plugins, this might take you a while to set up but it can handle realtine effects and you can pipe them to any jack-aware client. It's designed for music but you can use it on whatever you like.

---

