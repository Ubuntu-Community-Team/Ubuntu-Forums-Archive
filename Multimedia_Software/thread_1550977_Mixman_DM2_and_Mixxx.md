---
title: "Mixman DM2 and Mixxx"
date: 2010-08-11
forum: Multimedia Software
---

### Post by sbussy89 on 2010-08-11
Ubuntu is not recognizing my Mixman DM2. I installed the driver from [here]("http://sourceforge.net/projects/dm2linux/"), but when I plug it in my "MIDI Controllers" tab in the mixxx preferences says "No midi devices available." The person [here]("http://metrics.mixxx.org/forums/viewtopic.php?f=3&t=1552") was able to get it working, and I followed the same steps. Odd thing is my computer seems to not even notice the device... when I plug it in neither the device nor the computer show any indication of a connection. I know the device is good because when I plug it into my Windows box it is recognized immediately. Any help?

---

### Post by openversus on 2011-04-30
I have similar problem...
so I decided to post a reply...:D

I installed MIxxx 1.9 on Lucid:
I use a creative sound card soundblaster live 24-bit, which I use as a Master channel and the integrated sound card for headphones. This is because 'I can not enable the channel to the headphones of creative usb.
This is my first problem.
How can I manage Mixxx fully with the external sound card? :-({|=

I also decided to test Mixman DM2 and I installed the [_**driver**_ ]("http://sourceforge.net/projects/dm2linux/files/dm2linux/1.0_pre/dm2-source_1.0_all.deb/download") and I also do this command after installing it:
*sudo m-a a-i dm2-source*
with poor results.
Mixman is recognized and if I select in the preferences Midi, Mixman DM2 for linux I have this problem:
Some commands work, but for example the Crossfader manages the master channel 1 ... In short, it's alive, but the configuration file command, it contains errors.
Does anyone know how to set up and solve this problem?:confused:

---

### Post by openversus on 2011-05-04
Now I can mix music in Ubuntu 10.10 Lucid with Mixxx 1.9.0 (1.9.0-1~ppa1~lucid6) and DM2 Mixman. :D 
Everything works using also an external USB Creative SoundBlaster 24-bit.
But I need some siggestion:
1) that USB Creative SoundBlaster 24-bit has a lot of channel but in gnome alsa mixer I can only see PCM, Mic and CMSS and Power channels. How can I enable others channel, for example  for headphone? :shock: 
At the moment I select channel 1-2 for sound blaster and I insert my audio cable in front and it works as master. I use the integrated sound card as headphone at the moment.

2) I have some problem with DM2 Mixman:  :o 
using this mapping file:
```
<?xml version="1.0" encoding="utf-8"?>
<MixxxMIDIPreset mixxxVersion="1.7.0+" schemaVersion="1">
  <info>
    <name>Mixman DM2 (Linux)</name>
    <author>Jan Jockusch</author>
    <description>This is the DM2 mapping for the Linux driver (dm2linux.sourceforge.net)</description>
  </info>        
  <controller id="Mixman DM2 (Linux)">
    <scriptfiles>
      <file functionprefix="DM2" filename="Mixman DM2 (Linux).js"/>
    </scriptfiles>
    <controls>
      <!-- Wheels map to "scratch", but with different scaling, see script. -->
      <control>
        <status>0xb0</status>
        <midino>0x01</midino>
        <group>[Channel1]</group>
        <key>DM2.scratch1</key>
        <options>
          <script-binding/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x03</midino>
        <group>[Channel2]</group>
        <key>DM2.scratch2</key>
        <options>
          <script-binding/>
        </options>
      </control>

      <!-- Master controls -->

      <control>
        <status>0xb0</status>
        <midino>0x2</midino>
        <group>[Master]</group>
        <key>crossfader</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x79</midino>
        <group>[Master]</group>
        <key>volume</key>
        <options>
          <normal/>
        </options>
      </control>

      <!-- Flanger -->

      <control>
        <status>0x90</status>
        <midino>0x35</midino>
        <group>[Channel1]</group>
        <key>flanger</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x33</midino>
        <group>[Channel2]</group>
        <key>flanger</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x04</midino>
        <group>[Flanger]</group>
        <key>lfoDepth</key>
        <options>
          <normal/>
        </options>
      </control>
      <!-- We have a joystick with two axes, so use a key to shift one axis. -->
      <control> 
        <status>0x90</status>
        <midino>0x34</midino>
        <key>DM2.shift</key>
        <options>
          <script-binding/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x05</midino>
        <key>DM2.delay_period</key>
        <options>
          <script-binding/>
        </options>
      </control>

      <!-- Playlist controls and track loading -->

      <control>
        <status>0x90</status>
        <midino>0x41</midino>
        <group>[Playlist]</group>
        <key>SelectNextTrack</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x42</midino>
        <group>[Playlist]</group>
        <key>SelectPrevTrack</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x43</midino>
        <group>[Channel1]</group>
        <key>LoadSelectedTrack</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x44</midino>
        <group>[Channel2]</group>
        <key>LoadSelectedTrack</key>
        <options>
          <normal/>
        </options>
      </control>

      <!-- Basic controls Ch1 -->

      <control>
        <status>0x90</status>
        <midino>0x37</midino>
        <group>[Channel1]</group>
        <key>play</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x14</midino>
        <group>[Channel1]</group>
        <key>reverse</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x14</midino>
        <group>[Channel1]</group>
        <key>playposition</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x17</midino>
        <group>[Channel1]</group>
        <key>pregain</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x16</midino>
        <group>[Channel1]</group>
        <key>rate</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x16</midino>
        <group>[Channel1]</group>
        <key>rate_perm_up_small</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x15</midino>
        <group>[Channel1]</group>
        <key>rate_perm_down_small</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x3b</midino>
        <group>[Channel1]</group>
        <key>cue_default</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x15</midino>
        <group>[Channel1]</group>
        <key>volume</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x3f</midino>
        <group>[Channel1]</group>
        <key>back</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x3e</midino>
        <group>[Channel1]</group>
        <key>fwd</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x3d</midino>
        <group>[Channel1]</group>
        <key>pfl</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x3c</midino>
        <group>[Channel1]</group>
        <key>DM2.beatsync</key>
        <options>
          <script-binding/>
        </options>
      </control>

      <!-- Basic controls Ch2 -->

      <control>
        <status>0x90</status>
        <midino>0x36</midino>
        <group>[Channel2]</group>
        <key>play</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x24</midino>
        <group>[Channel2]</group>
        <key>reverse</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x24</midino>
        <group>[Channel2]</group>
        <key>playposition</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x27</midino>
        <group>[Channel2]</group>
        <key>pregain</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x26</midino>
        <group>[Channel2]</group>
        <key>rate</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x26</midino>
        <group>[Channel2]</group>
        <key>rate_perm_up_small</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x25</midino>
        <group>[Channel2]</group>
        <key>rate_perm_down_small</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x3a</midino>
        <group>[Channel2]</group>
        <key>cue_default</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x25</midino>
        <group>[Channel2]</group>
        <key>volume</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x30</midino>
        <group>[Channel2]</group>
        <key>back</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x31</midino>
        <group>[Channel2]</group>
        <key>fwd</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x32</midino>
        <group>[Channel2]</group>
        <key>pfl</key>
        <options>
          <normal/>
        </options>
      </control>

      <!-- Filtering controls -->

      <control>
        <status>0x90</status>
        <midino>0x10</midino>
        <group>[Channel1]</group>
        <key>filterHighKill</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x11</midino>
        <group>[Channel1]</group>
        <key>filterMidKill</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x12</midino>
        <group>[Channel1]</group>
        <key>filterLowKill</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x20</midino>
        <group>[Channel2]</group>
        <key>filterHighKill</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x21</midino>
        <group>[Channel2]</group>
        <key>filterMidKill</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0x90</status>
        <midino>0x22</midino>
        <group>[Channel2]</group>
        <key>filterLowKill</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x10</midino>
        <group>[Channel1]</group>
        <key>filterHigh</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x11</midino>
        <group>[Channel1]</group>
        <key>filterMid</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x12</midino>
        <group>[Channel1]</group>
        <key>filterLow</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x20</midino>
        <group>[Channel2]</group>
        <key>filterHigh</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x21</midino>
        <group>[Channel2]</group>
        <key>filterMid</key>
        <options>
          <normal/>
        </options>
      </control>
      <control>
        <status>0xb0</status>
        <midino>0x22</midino>
        <group>[Channel2]</group>
        <key>filterLow</key>
        <options>
          <normal/>
        </options>
      </control>
    </controls>



    <!-- Light show while playing a track -->
    <outputs>
      <output>
	<group>[Channel1]</group>
	<key>play</key>
	<status>0xB0</status>
	<midino>0x58</midino>
	<minimum>0.5</minimum>
      </output>
      <output>
	<group>[Channel2]</group>
	<key>play</key>
	<status>0xB0</status>
	<midino>0x59</midino>
	<minimum>0.5</minimum>
      </output>
    </outputs>
  </controller>
</MixxxMIDIPreset>
```
 
and this mapping: [http://www.mixxx.org/wiki/lib/exe/fetch.php/hardware:mixman_dm2_linux_map.png?cache=](http://www.mixxx.org/wiki/lib/exe/fetch.php/hardware:mixman_dm2_linux_map.png?cache=) I have this problem:
a) touching playpos/reverse, the song play reverse but touching again the song still remain in reverse mode 
b) joystick for dept or delay is not working
c)the key shift to period is not working

Waiting for your help I wish you... Buena Vida! :mrgreen:

---

