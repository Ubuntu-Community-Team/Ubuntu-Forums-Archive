---
title: "VLC player custom (preset) equalizer setup"
date: 2009-08-29
forum: Multimedia Software
---

### Post by dynamics on 2009-08-29
Hi friends

I could set up the equalizer in my vlc player but the problem I am facing is I cannot name it or save it as 'mine' or whatever name I want as one can do it in xmms (save as 'mine' or 'mine1' and then load 'mine' or 'mine1' etc whenever I want)

Secondly whenever I open a song to play in vlc it starts with default 'flat' equalizer configuration. Even if I set up my own equalizer settings it changes to 'default' when the next track begins. This drives me crazy because I have to again and again repeat the following set of operations for each song in a playlist

1) 'Tools' --> 'Extended Settings' -->Tab 'Graphic Equalizer' --> Tick 'Enable'
2) Then start setting the gain, bass, treble etc .... 

I have to repeat the above settings for each and every song in a play list :-(

Where as in XMMS one can set up his/her custom equilizer settings and name it and save it. Whenever needed that setting cane be loaded.

In one sentence what I want is how to make the vlc player equalizer work similar to 'XMMS'

As an **Alternate **solution how can I change the settings of 'Flat' equalizer frequencies in VLC?

Thanks 

PS: Why I want to do it is the default settings of 'XMMS' frequency bands are not good as compared to vlc player equilizer frequency settings (or tone quality)

---

### Post by mc4man on 2009-08-30
> In one sentence what I want is how to make the vlc player equalizer work similar to 'XMMS'

Not possible in one sentence, nor likely to work similar


So forgive me for extra lines

If you have vlc 0.9.9a or higher (maybe 0.9.8, don't remember

Lower versions of 0.9.x the equalizer is broken

There are 'global' settings, (tools -> preferences), and 'local' settings (from gui)

1st you enable and set the equalizer in tools -> preferences -> click "all" -> audio -> filters. There you click the box for "Equalizer with 10 bands"

(this will enable it globally, ie. every time you open vlc it will be enabled

Then expand filters and either pick a preset to be globally set or enter your 10 band settings in the box for a custom one ( you only can set one, again this is a global setting

The format is 10 values between -20 and 20 separated by spaces, you can use decimals.

If you use the custom box or a preset  it will be your default when opening vlc unless after opening vlc you open the equalizer from the gui's extended setting. Then whatever is set there will override locally (per session

You can check/confirm, but not set, your settings in ~/.config/vlc/vlcrc

(open in text editor, use find - equalizer, maybe click find 3 times to get to settings


Overall a pita for the custom, easy for the presets.

The problem may be you don't like any of the presets.

What would be fairly easy to do, if you build your own vlc is create and name your own. The source file for the presets is very easy to read and redo.
Am including some of "equalizer_presets.h" so you can see the values set (from 0.9.9a
> 
static const eqz_preset_t eqz_preset_flat_10b=
{
    "flat", 10, 12.0,
    { 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 },
};
static const eqz_preset_t eqz_preset_classical_10b=
{
    "classical", 10, 12.0,
    { -1.11022e-15, -1.11022e-15, -1.11022e-15, -1.11022e-15, -1.11022e-15, -1.11022e-15, -7.2, -7.2, -7.2, -9.6 }
};
static const eqz_preset_t eqz_preset_club_10b=
{
    "club", 10, 6.0,
    { -1.11022e-15, -1.11022e-15, 8, 5.6, 5.6, 5.6, 3.2, -1.11022e-15, -1.11022e-15, -1.11022e-15 }
};
static const eqz_preset_t eqz_preset_dance_10b=
{
    "dance", 10, 5.0,
    { 9.6, 7.2, 2.4, -1.11022e-15, -1.11022e-15, -5.6, -7.2, -7.2, -1.11022e-15, -1.11022e-15 }
};
static const eqz_preset_t eqz_preset_fullbass_10b=
{
    "fullbass", 10, 5.0,
    { -8, 9.6, 9.6, 5.6, 1.6, -4, -8, -10.4, -11.2, -11.2  }
};
static const eqz_preset_t eqz_preset_fullbasstreble_10b=
{
    "fullbasstreble", 10, 4.0,
    { 7.2, 5.6, -1.11022e-15, -7.2, -4.8, 1.6, 8, 11.2, 12, 12 }
};

static const eqz_preset_t eqz_preset_fulltreble_10b=
{
    "fulltreble", 10, 3.0,
    { -9.6, -9.6, -9.6, -4, 2.4, 11.2, 16, 16, 16, 16.8 }
};
static const eqz_preset_t eqz_preset_headphones_10b=
{
    "headphones", 10, 4.0,
    { 4.8, 11.2, 5.6, -3.2, -2.4, 1.6, 4.8, 9.6, 12.8, 14.4 }
};
static const eqz_preset_t eqz_preset_largehall_10b=
{
    "largehall", 10, 5.0,
    { 10.4, 10.4, 5.6, 5.6, -1.11022e-15, -4.8, -4.8, -4.8, -1.11022e-15, -1.11022e-15 }
};
static const eqz_preset_t eqz_preset_live_10b=
{
    "live", 10, 7.0,
    { -4.8, -1.11022e-15, 4, 5.6, 5.6, 5.6, 4, 2.4, 2.4, 2.4 }
};
static const eqz_preset_t eqz_preset_party_10b=
{
    "party", 10, 6.0,
    { 7.2, 7.2, -1.11022e-15, -1.11022e-15, -1.11022e-15, -1.11022e-15, -1.11022e-15, -1.11022e-15, 7.2, 7.2 }
};
static const eqz_preset_t eqz_preset_pop_10b=
{
    "pop", 10, 6.0,
    { -1.6, 4.8, 7.2, 8, 5.6, -1.11022e-15, -2.4, -2.4, -1.6, -1.6 }
};
static const eqz_preset_t eqz_preset_reggae_10b=
{
    "reggae", 10, 8.0,
    { -1.11022e-15, -1.11022e-15, -1.11022e-15, -5.6, -1.11022e-15, 6.4, 6.4, -1.11022e-15, -1.11022e-15, -1.11022e-15 }
};
static const eqz_preset_t eqz_preset_rock_10b=
{
    "rock", 10, 5.0,
    { 8, 4.8, -5.6, -8, -3.2, 4, 8.8, 11.2, 11.2, 11.2 }
};
static const eqz_preset_t eqz_preset_ska_10b=
{
    "ska", 10, 6.0,
    { -2.4, -4.8, -4, -1.11022e-15, 4, 5.6, 8.8, 9.6, 11.2, 9.6 }
};
static const eqz_preset_t eqz_preset_soft_10b=
{
    "soft", 10, 5.0,
    { 4.8, 1.6, -1.11022e-15, -2.4, -1.11022e-15, 4, 8, 9.6, 11.2, 12 }
};
static const eqz_preset_t eqz_preset_softrock_10b=
{
    "softrock", 10, 7.0,
    { 4, 4, 2.4, -1.11022e-15, -4, -5.6, -3.2, -1.11022e-15, 2.4, 8.8 }
};
static const eqz_preset_t eqz_preset_techno_10b=
{
    "techno", 10, 5.0,
    { 8, 5.6, -1.11022e-15, -5.6, -4.8, -1.11022e-15, 8, 9.6, 9.6, 8.8 }
};

static const eqz_preset_t *eqz_preset_10b[] =
{
    &eqz_preset_flat_10b,
    &eqz_preset_classical_10b,
    &eqz_preset_club_10b,
    &eqz_preset_dance_10b,
    &eqz_preset_fullbass_10b,
    &eqz_preset_fullbasstreble_10b,
    &eqz_preset_fulltreble_10b,
    &eqz_preset_headphones_10b,
    &eqz_preset_largehall_10b,
    &eqz_preset_live_10b,
    &eqz_preset_party_10b,
    &eqz_preset_pop_10b,
    &eqz_preset_reggae_10b,
    &eqz_preset_rock_10b,
    &eqz_preset_ska_10b,
    &eqz_preset_soft_10b,
    &eqz_preset_softrock_10b,
    &eqz_preset_techno_10b,
    NULL

Note 
vlc uses this quite often as a value, don't have a clue as to what makes it different from -1.11

-1.11022e-15

---

### Post by dynamics on 2009-08-30
Hi Five to [mc4man]("http://ubuntuforums.org/member.php?u=320715")

Thats fantastic.... I got what I wanted ... even more than what I expected after 2 months of rigorous googling. 

Thank you very much. 
Now I can play around with my own settings :-)
Thanks again.     
:KS

---

### Post by calanor on 2009-08-31
i was having the same problem for quite a time now and after googling i came to this page 
but i can not find the file vlcrc where is it located in ubuntu 9.04, i installed from add/remove

---

### Post by calanor on 2009-08-31
okay saved the settings and they are working

---

