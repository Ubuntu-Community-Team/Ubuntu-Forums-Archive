---
title: "What Have They Done To My Song?"
date: 2021-11-23
forum: Multimedia Software
---

### Post by ulrichmuc2 on 2021-11-23
I have audacious running as internet radio, listening always to the same station.
I switch on and off using the power switch of the amplifyer.
That is the most convenient way, as audacious is running on a a headless Raspberry PI.
However, after about 17 hours audacious stops producing sound.
I tried with a script that did "ps -e | grep audacious" every 60 seconds, to find out what happened when.
But the process is still running, just not producing output.
When I kill the process and restart, everything is fine till the next morning.
audacious is started with "nohup audacious -H <URL> &".

Any ideas?

---

### Post by KBar on 2021-11-23
What's the version of Ubuntu and does it run PulseAudio?

---

### Post by ulrichmuc2 on 2021-11-23
The System manager says:
18.04.6 LTS 64 bit
Memory 3.7 GB
Available disk space 10.3 GB

ps -e | grep psm
gives: pulseaudio

---

### Post by KBar on 2021-11-23
```
pulseaudio --check
pulseaudio --version
```

Run the first command. If there is no output (return code 0), then it's up and running.

I don't think I can help you directly, but it's always a good practice to look at logs. Run it with these options:
```
pulseaudio --log-level=4 --log-target=newfile:PATH --start
```
where _PATH_ is either /tmp/pa.log or $HOME/pa.log, or anywhere you usually store your logs. Check this log after the problem occurs and see if there's anything suspicious.

If you have issues with that, try this [https://askubuntu.com/a/142868/1044722](https://askubuntu.com/a/142868/1044722)

---

### Post by ulrichmuc2 on 2021-11-23
Yes, it is up and running. Version is 11.1

---

