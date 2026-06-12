---
title: "Virtual Surround Sound Software"
date: 2015-03-04
forum: Multimedia Software
---

### Post by mcharitos on 2015-03-04
Hello there

I'd like to ask if you know any program for Ubuntu that mimics Surround Sound on Stereo Headphones. For e.g. my SONY TV has an option called "Dolby Virtual" and though it actually has two speakers, if you choose this option, you are getting the impression that sound comes from more than two sources. Also, i had a similar program on Windows (though i don't recall it's name)

So, is there any Virtual Surround Sound software for Ubuntu to use with your stereo headphones/speakers, or do we have to wait for that?

Thank you

---

### Post by mcharitos on 2015-03-09
So i was searching on the internet and i found the two following suggestions to enable virtual surround [https://rudd-o.com/linux-and-free-software/how-to-get-virtual-surround-sound-on-your-headphones-plugged-to-your-linux-rig](https://rudd-o.com/linux-and-free-software/how-to-get-virtual-surround-sound-on-your-headphones-plugged-to-your-linux-rig) and [http://www.rpgameplace.de/blog/index.php?/archives/25-Virtual-Surround-for-stereo-headphones-with-ALSA.html](http://www.rpgameplace.de/blog/index.php?/archives/25-Virtual-Surround-for-stereo-headphones-with-ALSA.html)

As usual i have to insert commands in the Terminal. I tried both.
The thing with the first one, is that somewhere in the process i find out i have to first install "yum". Done that, but when i insert the command " yum install -y alsa-plugins-vdownmix " it tells me that "i need to be root to perform this command". So, after some search again, i do that too (after i create a password- which i had to search for that as well), but then tells me
" Run "yum repolist all" to see the repos you have. You can enable repos with yum-config-manager --enable <repo> "
i'm doing that too only to get the reply " repolist: 0 "
which i have no idea what that means, so i give up.
I also tried the second solution with about the same results.

Ubuntu are great and everything. But still, after another failure, i wonder why in 2015 whenever i have to install something, i'm forced to use DOS, when the Windows users all they have to do is point with their arrow on an install button. I hope this will change, cause it's a complicated way to do(?) simple staff

---

### Post by KillerKelvUK on 2015-03-10
<snip>

Top link has all you need, if you're running an up-to-date Ubuntu distro odds are that you already have the software installed, it just needs configuring.

For what its worth...The Apple App Store is Apples software install tool like Google Play is Google's software tool.  Ubuntu has Aptitude (use apt-get in the command line...not DOS!) or for the Windoze folk its Software Centre for your point and clicks.  Fedora and others (linux distros but not Ubuntu) use yum as their command line app stores.

EDIT:

Also think you'd have better luck moving this thread into the Multimedia or General Help forum sections, your question doesn't relate to the same Virtualisation topic this forum section is about.

---

### Post by papibe on 2015-03-10
Thread moved to **Multimedia** subforum.

---

### Post by mcharitos on 2015-03-10
> [http://lmgtfy.com/?q=ubuntu+virtual+surround+sound](http://lmgtfy.com/?q=ubuntu+virtual+surround+sound)

@ KillerKelvUK I was so excited when i saw that link... only to find out it's the google search bar... -_-;
btw the first result "*Ubuntu 14.04 - Virtual Surround Sound? - Ask Ubuntu*" is where i found this [http://www.rpgameplace.de/blog/index...with-ALSA.html]("http://www.rpgameplace.de/blog/index.php?/archives/25-Virtual-Surround-for-stereo-headphones-with-ALSA.html") which i already mentioned. The article there, sais that the answer to my request, lies in "a plugin for ALSA called *vdownmix*", which i have no idea what that is and how am i supposed to find it (I'm running Lubuntu 14.10,so they probably have ALSA)
Anyway, maybe the lack of an easily installed (at least the way i want it to) virtual surround software is not much of a problem. After all, i'm happy with this OS and the programs that come with it (Gimp, Inkscape, Scribus, Libre Office to name a few). And the Software Center is like a dream come true

As for the Aptitude/DOS thing... however you name it, when i have to input commands in front of a black screen, makes no difference to me. I'll always prefer not to

p.s. i send a message to move the thread, as i can't do it myself cause i'm not a forum staff. Sorry if i messed up

EDIT
that was fast! thank you papibe

---

### Post by pramuka81 on 2015-03-14
Open terminal and type "sudo gedit". Copy paste the following:

pcm.!surround51 {
        @args [ CARD DEV ]
        @args.CARD {
                type string
                default {
                        @func getenv
                        vars [
                                ALSA_SURROUND51_CARD
                                ALSA_PCM_CARD
                                ALSA_CARD
                        ]
                        default {
                                @func refer
                                name defaults.pcm.surround51.card
                        }
                }
        }
        @args.DEV {
                type integer
                default {
                        @func igetenv
                        vars [
                                ALSA_SURROUND51_DEVICE
                        ]
                        default {
                                @func refer
                                name defaults.pcm.surround51.device
                        }
                }
        }
        type vdownmix
        slave.pcm {
                @func refer
                name {
                        @func concat
                        strings [
                                "cards."
                                {
                                        @func card_driver
                                        card $CARD
                                }
                                ".pcm.surround51." $DEV ":CARD=" $CARD
                        ]
                }
        }
        hint {
                description "Downmix to stereo 5.1 Surround output to Front, Center, Rear and Subwoofer speakers"
                device $DEV
        }
}


pcm.!surround40 {
        @args [ CARD DEV ]
        @args.CARD {
                type string
                default {
                        @func getenv
                        vars [
                                ALSA_SURROUND51_CARD
                                ALSA_PCM_CARD
                                ALSA_CARD
                        ]
                        default {
                                @func refer
                                name defaults.pcm.surround40.card
                        }
                }
        }
        @args.DEV {
                type integer
                default {
                        @func igetenv
                        vars [
                                ALSA_SURROUND51_DEVICE
                        ]
                        default {
                                @func refer
                                name defaults.pcm.surround40.device
                        }
                }
        }
        type vdownmix
        slave.pcm {
                @func refer
                name {
                        @func concat
                        strings [
                                "cards."
                                {
                                        @func card_driver
                                        card $CARD
                                }
                                ".pcm.surround51." $DEV ":CARD=" $CARD
                        ]
                }
        }
        hint {
                description "Downmix to stereo 4.0 Surround output to Front, Center, Rear and Subwoofer speakers"
                device $DEV
        }
}


Save as "asound.conf" at /etc

After that, for customize the surround effect, you may need to install Veromix (available on Ubuntu Software Center).
You can add some effect plugins and make some configuration such as in the following picture.
[IMG]http://oi61.tinypic.com/r7kw1h.jpg[/IMG]
(Macbuntu Vivid Vervet)

Open the Sound Settings and choose the new (virtual) sound device. :)

---

