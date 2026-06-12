---
title: "Application not detecting video card capabilities"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by The Saxman on 2008-03-06
Hello,

I am about ready to either scream, or cry. I don't know which.

Here are my system specs:
3gig Pentium 4
1gig of DDR ram
256Mb ATI Radeon X600 graphics card
2 40gig hard drives
WMP300N Linksys Wireless network adaptor

OK a little history:

I had been driven nearly to mental breakdown and rage with "some other operating system" because of the crashes and bugs, so I had a friend suggest that I try Ubuntu Linux. Not sure if I could handle it, I decided to dual boot for a while and test it out. Apparently I installed Ubuntu 7.04 just a couple weeks before 7.10 came out because it told me to update after about 2 weeks. I decided that I didn't want to bother wiping my computer and doing a fresh install so I let it update. I was stuck at 1024x768 resolution but other than that I didn't have any major problems. I decided this week that I had had enough of "that other operating system" (I hadn't used it for a couple months), so I was going to start from scratch. 

I downloaded and burned and checked for errors the Desktop CD for Ubuntu 7.10. I wiped my computer with Darik's Boot and Nuke. Then I installed Ubuntu and updated it. Then I installed ndiswrapper and got my wireless working (with a LOT less trouble than last time. Yay!) So I then installed the proprietary drivers for my graphics card. It all seemed to be working much better than before. I could actually use the special effects. Things seemed to move much smoother. The resolution was no longer stuck at 1024x768. Then I decided to set the screen saver to my favorite, colorfire.

That was the start of my troubles. When the screen saver activates it is TERRIBLY jerky and slow and it takes about 30 seconds to break it. I couldn't even change the screen saver, when I opened the screen saver manager it threw me back to the login screen. I finally was told by someone to try reinstalling something (I'm sorry, I don't remember what it was. It had something to do with "gl") with synaptic and quickly change to black screen. I did, and now the computer doesn't lock up. I miss my favorite screen saver. :(

Next I tried installing Eternal Lands, a MMORPG that I have enjoyed for a couple years now. It won't work. It DID work before I reinstalled. Nothing about the game has changed, it is the same version and same installation procedure that I followed last time. Before I reinstalled, when I opened the game it said:

[COLOR="Teal"]GL_ARB_multitexture extension found, using it.
GL_ARB_texture_env_combine extension found, using it,
GL_EXT_compiled_vertex_array extension found, using it,
GL_ARB_point_sprite extension found, using it,
GL_ARB_texture_compression extension found, using it,
GL_EXT_texture_compression_s3tc extension found, using it,
GL_SGIS_generate_mipmap extension found, using it,
GL_ARB_shadow extension found, using it,
GL_ARB_vertex_buffer_object extension found, using it,
GL_EXT_framebuffer_object extension found, using it,
GL_EXT_draw_range_elements extension found, using it,[/COLOR]
[COLOR="Red"]Couldn't find the GL_ARB_texture_non_power_of_two extension, not using it...[/COLOR]
[COLOR="Teal"]GL_ARB_fragment_program extension found, using it,
GL_ARB_vertex_program extension found, using it,
GL_ARB_fragment_shader extension found, using it,
GL_ARB_vertex_shader extension sound, using it,
GL_ARB_shader_objects extension found, using it,
GL_ARB_shading_language_100 extension found, using it,
GL_ARB_texture_mirrored_repeat extension found, using it,
GL_ARB_texture_rectangle extension, using it,
GL_EXT_fog_coord extension found, using it,[/COLOR]
[COLOR="Red"]Couldn't find the GL_ATI_texture_compression_3dc extension, not using it,
Couldn't find the GL_EXT_texture_compression_latc extension, not using it,[/COLOR]

And when using the Windows version of the game in Wine only the non_power_of_two wasn't found.

Now after reinstalling Ubuntu, when I try starting Eternal Lands is says:

[COLOR="Teal"]GL_ARB_multitexture extension found, using it.
GL_ARB_texture_env_combine extension found, using it,[/COLOR]
[COLOR="Red"]Couldn't find the GL_EXT_compiled_vertex_array extension found, using it,
Couldn't find the GL_ARB_point_sprite extension found, using it,
Couldn't find the GL_ARB_texture_compression extension found, using it,
Couldn't find the GL_EXT_texture_compression_s3tc extension found, using it,
Couldn't find the GL_SGIS_generate_mipmap extension found, using it,
Couldn't find the GL_ARB_shadow extension found, using it,
Couldn't find the GL_ARB_vertex_buffer_object extension found, using it,
Couldn't find the GL_EXT_framebuffer_object extension found, using it,
Couldn't find the GL_EXT_draw_range_elements extension found, using it,
Couldn't find the GL_ARB_texture_non_power_of_two extension, not using it...
Couldn't find the GL_ARB_fragment_program extension found, using it,
Couldn't find the GL_ARB_vertex_program extension found, using it,
Couldn't find the GL_ARB_fragment_shader extension found, using it,
Couldn't find the GL_ARB_vertex_shader extension sound, using it,
Couldn't find the GL_ARB_shader_objects extension found, using it,
Couldn't find the GL_ARB_shading_language_100 extension found, using it,
Couldn't find the GL_ARB_texture_mirrored_repeat extension found, using it,
Couldn't find the GL_ARB_texture_rectangle extension, using it,
Couldn't find the GL_EXT_fog_coord extension found, using it,
Couldn't find the GL_ATI_texture_compression_3dc extension, not using it,
Couldn't find the GL_EXT_texture_compression_latc extension, not using it,[/COLOR]
[COLOR="Teal"]Compiled Vertex Arrays disabled.
Point Particles disabled.[/COLOR]
[COLOR="Red"]Frambuffer disabled (need newer driver)[/COLOR]
[COLOR="Yellow"]Shadow map size not supported! Shadow map size reduced to 512![/COLOR]
[COLOR="Red"]Shadowmapping disabled (need newer hardware)[/COLOR]

Then when I log in the game crashes back to the Desktop.

Any help would be GREATLY appreciated!!

Thanks!
The Saxman

---

