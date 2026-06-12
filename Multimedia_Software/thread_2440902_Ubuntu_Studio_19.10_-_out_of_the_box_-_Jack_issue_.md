---
title: "Ubuntu Studio 19.10 - out of the box - Jack issue (choppy audio)"
date: 2020-04-16
forum: Multimedia Software
---

### Post by lucedan on 2020-04-16
I just installed my Ubuntu Studio 19.10. I upgraded all things apart for the Kernel (as updating the kernel was crashing Jack completely). So my kernel right now is 5.3.0-18
  I installed the software SuperCollider. To do so, I installed the following:
  ```
sudo apt-get install build-essential libsndfile1-dev libasound2-dev libavahi-client-dev libicu-dev libreadline6-dev libfftw3-dev libxt-dev libudev-dev pkg-config git cmake qt5-default qt5-qmake qttools5-dev qttools5-dev-tools qtdeclarative5-dev qtpositioning5-dev libqt5sensors5-dev libqt5opengl5-dev qtwebengine5-dev libqt5svg5-dev libqt5websockets5-dev

sudo apt-get install libjack-jackd2-dev

```  The installation went through nicely. However, when starting Jack, Jack is stuttering at lengths of half a second.
  It's months that I am having this issue, and I don't understand why.  Is there anybody that can help me solve it? (P.S., my computer is a  Lenovo C640. I had the same computer 5 months ago - which got broken -  and Jack was running fine).

---

