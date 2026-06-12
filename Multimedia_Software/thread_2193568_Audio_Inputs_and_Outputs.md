---
title: "Audio Inputs and Outputs"
date: 2013-12-13
forum: Multimedia Software
---

### Post by BIGTLyons on 2013-12-13
Hello, this is my very first post on here, I've used every version of Ubuntu since 9 and I have a have a little bit of know how with command line and stuff.
But anyways, I have a Dell Latitude D520 with regular Ubuntu 12.04. Everything works great on it. However, I enjoy making music on a Kaossilator Pro.
Basically what I want to do is figure out a way to make the sound going into the microphone jack to come out of the headphone jack, with as little latency as possible. How can I configure my computer to do that? I have already downloaded JACK, and Ardour, but I cannot get JACK to run without errors. Is there any alternative way to go about this?

---

### Post by tgalati4 on 2013-12-14
Install some different mixers and see which one will allow you to mix the input into the headphone channel as a "monitor".

Open a terminal:

```
apt-cache search mixer
```

The other way to do it is to get a small, analog headphone mixer and patch the input into that.  Basically monitor the analog signal outside of the computer.  

I have one of these and they work well:  [http://www.aphex.com/products/headpod-4/](http://www.aphex.com/products/headpod-4/)

That frees up the computer cycles for creating beats and capturing them, rather than processing the feedback channel.

---

