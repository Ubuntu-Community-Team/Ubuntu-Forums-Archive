---
title: "Latest updates broke Facebook Video and Soundcloud in Firefox"
date: 2014-11-27
forum: Multimedia Software
---

### Post by Ari-RootPCs on 2014-11-27
Running 14.04 - After updating to the latest Ubuntu images 2 days ago, suddenly playback for FB videos and Soundcloud (so far) only goes for about 30 seconds before stopping.  On Soundcloud, it skips to the next in the playlist and also only goes for ~30 seconds.

Youtube works fine, so I wouldn't think it's a Flash issue, just to be sure, I checked and it's 11.2.202.424, but Chromium things appear to be working fine and it has its own Flash player (Pepper 15.0.0.239)

I really don't want to be relying on Chromium, since lately it's been a huge resource suck and on top of that I keep getting "Aw Snap"  on roughly 1/3 of all pages after a minute even after trying all their suggested fixes.

---

### Post by Ari-RootPCs on 2014-11-30
Vimeo just straight up won't play at all - just throws a black screen insde the player as soon as I click on the image

Liveleak gooes into a buffering zone and never starts

I've tested out a few browser Flash games to make sure, and the ones I've tried all seem to work.

Is it possible that these are all using something other than Flash, like OpenH264?  That's at v1.1, if it matters.

---

### Post by Yellow Pasque on 2014-12-01
html5?

---

### Post by Ari-RootPCs on 2014-12-01
From html5test.com:

Your browser scores 475 out of 555 points

Semantics
Parsing rules
10
<!DOCTYPE html> triggers standards mode
	
Yes &#10004;
HTML5 tokenizer
	
Yes &#10004;
HTML5 tree building
	
Yes &#10004;
HTML5 defines rules for embedding SVG and MathML inside a regular HTML document. Support for SVG and MathML is not required though, so no actual points are awarded if your browser supports embedding these two technologies.
SVG in text/html
	
Yes &#10004;
MathML in text/html
	
Yes &#10004;
Elements
21/30
Embedding custom non-visible data
	
Yes &#10004;
New or modified elements
Section elements
	
Yes &#10004;
Grouping content elements
	
Yes &#10004;
Text-level semantic elements
	
Partial &#9675;
Interactive elements
	
No &#10008;
Global attributes or methods
hidden attribute
	
Yes &#10004;
Dynamic markup insertion
	
Yes &#10004;
Forms
75/110
Field types
input type=text
	
Yes &#10004;
input type=search
	
Yes &#10004;
input type=tel
	
Yes &#10004;
input type=url
	
Yes &#10004;
input type=email
	
Yes &#10004;
input type=date
	
No &#10008;
input type=month
	
No &#10008;
input type=week
	
No &#10008;
input type=time
	
No &#10008;
input type=datetime
	
No &#10008;
input type=datetime-local
	
No &#10008;
input type=number
	
Yes &#10004;
input type=range
	
Yes &#10004;
input type=color
	
Yes &#10004;
input type=checkbox
	
Yes &#10004;
input type=image
	
Yes &#10004;
input type=file
	
Yes &#10004;
textarea
	
Yes &#10004;
select
	
Yes &#10004;
fieldset
	
Yes &#10004;
datalist
	
Yes &#10004;
keygen
	
No &#10008;
output
	
Yes &#10004;
progress
	
Yes &#10004;
meter
	
Yes &#10004;
Fields
Field validation
	
Yes &#10004;
Association of controls and forms
	
Partial &#9675;
Other attributes
	
Partial &#9675;
CSS selectors
	
Partial &#9675;
Events
	
Yes &#10004;
Forms
Form validation
	
Yes &#10004;
Microdata
5
Microdata
	
Yes &#10004;
Device Access
Location and Orientation
20
Geolocation
	
Yes &#10004;
Device Orientation
	
Yes &#10004;
Output
10
Full screen support
	
Prefixed &#10004;
Web Notifications
	
Yes &#10004;
Input
15/20
Access the webcam
	
Prefixed &#10004;
Gamepad control
	
Yes &#10004;
Pointer Events
	
No &#10008;
Pointer Lock support
	
Prefixed &#10004;
Performance & Integration
User interaction
22/25
Drag and drop
Attributes
	
Partial &#9675;
Events
	
Yes &#10004;
HTML editing
Editing elements
	
Yes &#10004;
Editing documents
	
Yes &#10004;
CSS selectors
	
No &#10008;
APIs
	
Yes &#10004;
Spellcheck
spellcheck attribute
	
Yes &#10004;
Performance
25
Native binary data
	
Yes &#10004;
Workers
Web Workers
	
Yes &#10004;
Shared Workers
	
Yes &#10004;
Security
28/40
Web Cryptography API
	
No &#10008;
Content Security Policy 1.0
	
Yes &#10004;
Content Security Policy 1.1
	
No &#10008;
Cross-Origin Resource Sharing
	
Yes &#10004;
Cross-document messaging
	
Yes &#10004;
Iframes
Sandboxed iframe
	
Yes &#10004;
Seamless iframe
	
No &#10008;
iframe with inline contents
	
Yes &#10004;
History and navigation
10
Session history
	
Yes &#10004;
Multimedia
Video
33/35
video element
	
Yes &#10004;
DRM support
	
No &#10008;
Media Source extensions
	
No &#10008;
Subtitle support
	
Yes &#10004;
Poster image support
	
Yes &#10004;
Codec detection
	
Yes &#10004;
The following tests go beyond the requirements of the HTML5 specification and are not counted towards the total score.
MPEG-4 support
	
No &#10008;
H.264 support
	
Yes &#10004;
Ogg Theora support
	
Yes &#10004;
WebM with VP8 support
	
Yes &#10004;
WebM with VP9 support
	
Yes &#10004;
Audio
25/30
audio element
	
Yes &#10004;
Web Audio API
	
Yes &#10004;
Speech Recognition
	
No &#10008;
Speech Synthesis
	
No &#10008;
The following tests go beyond the requirements of the HTML5 specification and are not counted towards the total score.
PCM audio support
	
Yes &#10004;
AAC support
	
Yes &#10004;
MP3 support
	
Yes &#10004;
Ogg Vorbis support
	
Yes &#10004;
Ogg Opus support
	
Yes &#10004;
WebM with Vorbis support
	
Yes &#10004;
WebM with Opus support
	
Yes &#10004;
Peer To Peer
15
WebRTC
	
Prefixed &#10004;
Data channel
	
Prefixed &#10004;
3D, Graphics & Effects
2D Graphics
21/25
Canvas 2D graphics
	
Yes &#10004;
Drawing primitives
Text support
	
Yes &#10004;
Path support
	
Yes &#10004;
Ellipse support
	
No &#10008;
Dashed line support
	
Yes &#10004;
Features
Hit testing support
	
No &#10008;
Blending modes
	
Yes &#10004;
Image export formats
PNG support
	
Yes &#10004;
JPEG support
	
Yes &#10004;
JPEG-XR support
	
No &#10008;
WebP support
	
No &#10008;
3D Graphics
20/25
WebGL 3D graphics
	
Yes &#10004;
WebGL 2 3D graphics
	
No &#10008;
Animation
5
window.requestAnimationFrame
	
Yes &#10004;
Connectivity
Communication
35
Server-Sent Events
	
Yes &#10004;
XMLHttpRequest Level 2
Upload files
	
Yes &#10004;
Response type support
	
Yes &#10004;
WebSocket
Basic socket communication
	
Yes &#10004;
ArrayBuffer and Blob support
	
Yes &#10004;
Offline & Storage
Web applications
20
Application Cache
	
Yes &#10004;
Custom scheme handlers
	
Yes &#10004;
Custom content handlers
	
Yes &#10004;
Custom search providers
	
Yes &#10004;
Storage
30
Key-value storage
Session Storage
	
Yes &#10004;
Local Storage
	
Yes &#10004;
Database storage
IndexedDB
	
Yes &#10004;
Objectstore Blob support
	
Yes &#10004;
Objectstore ArrayBuffer support
	
Yes &#10004;
The Web SQL Database specification is no longer being updated and has been replaced by IndexedDB. Because at least 3 vendors have shipped implementations of this specification we still include it in this test.
Web SQL Database
	
No &#10008;
Files
10
File API
	
Yes &#10004;
The Directories and System API proposal has failed to gain traction among browser vendors and is only supported in some Webkit based browsers. No additional points are awarded for supporting this API.
File API: Directories and System
	
No &#10008;
Other
Other
20
Styling
Scoped style element
	
Yes &#10004;
Scripts
Asyncronous script execution
	
Yes &#10004;
Runtime script error reporting
	
Yes &#10004;
Script execution events
	
Yes &#10004;
Base64 encoding and decoding
	
Yes &#10004;
JSON encoding and decoding
	
Yes &#10004;
Mutation Observer
	
Yes &#10004;
Other
Page Visibility
	
Yes &#10004;
Text selection
	
Yes &#10004;
Scroll into view
	
Yes &#10004;

---

### Post by Yellow Pasque on 2014-12-01
> No &#10008;
H.264 support

Have you tried disabling OpenH264 plugin? Firefox on Linux shouldn't need that, because it can use gstreamer to play h264 assuming gstreamer1.0-libav package is installed and Firefox's "media.gstreamer.enabled" key is set to true (I think Ubuntu has had it default to true for a few FF releases).

I use Debian with generic FF (aka iceweasel) 33.x and I get the same score in the html5 test, but h264 shows as supported for me.

EDIT: I did a quick test with openh264 and it will fail the html5 test unless gstreamer is enabled/working.

---

### Post by Ari-RootPCs on 2014-12-09
I disabled the 264 plugin, this is now after a general update today, including an update to Firefox 34 and a bunch of various lib files.  The weird part was that last night, after a reboot of the machine, things were working fine and worked properly, after the update today once again broken the same way, reboot didn't help.  Should have left well enough alone, eh?  I'm not a noob here but I really have no idea what the hell is going on with this. Maybe I shou8ld try to rollback?

---

