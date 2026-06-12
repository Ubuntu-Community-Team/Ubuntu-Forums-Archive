---
title: "Blender: how to create game with menu (some steps)"
date: 2015-01-07
forum: Multimedia Software
---

### Post by Claus7 on 2015-01-07
Dear all,

I wanted to create a basic game using blender. This game was about to entail animation, a menu and in the end to save it as a standalone application. I would like to write some steps I followed in order to reach that goal:


**1) What is blender?**

An open source 3D graphics and animation software.

**2) Can I use different environment?**

Yes, for example c++ with opengl using freeglut library.

**3) I would like to create an animation and see how it is looking like.**

In order to do that you will have to press the button P, while your mouse cursor is on the main window of blender. If you would like to return back in order to modify more your project, then you will have to press escape.

**4) I'm changing the transparency of a material, yet, I cannot see any change in edit/object mode.**

You won't see it. You will be able to see that change though, if you actually render your project.

[B]5) I have created a menu and I want to add a background to it. Is it possible?
[/B]
edit:
Yes it is. You will have to choose that object/shape that will be the canvas of your background. Before that choose texture mode.
Split the image area, by dragging the top right corner of your image area on the left. On the new area select: UV image editor.
From there pick up the image you want to add as background.
Now go to the left hand side image, choose edit mode and then press U and choose: project from view.
The image on the right hand size should be transfered to the left. You can make adjustments if you like.
Now, if you go to object mode your image should be crisp while added as a background to your plane.
The following guidelines will help you for step 6.

Going on the right hand side and:
Go to material and add a new one. Then,
under the button texture click new (the middle icon should be selected on top of that), and as type choose: Image or movie. Click open. Then again under texture go slightly below under mapping and as coordinates choose: UV and underneath that: 

you will find under the tab image the: open file browser button, which will help you to choose the image you want to add as a background.

**6) I'm done with my project, yet if I transfer my standalone game file to another folder I cannot see the background of my menu.What had happened?**

Following step 5 you will see that there is a button that says: save an image packed in the .blend file to disk. If you click it, your standalone file won't need to be with the background image at the same folder to work.

**7) What is a standalone file?**

A standalone file is the file of your game. If you create it, you will be able to run it as a standalone application. You might be able to give it to a friend so as for your friend to run your game. I do not know if this can happen for different OS though.

**8) How do I create a standalone file?**

There is a bug with version 2.69 (default version) for ubuntu 14.04
 i) tackle with the bug
Go to /usr/share/blender/scripts/addons and there, with root privileges, open the file game_engine_save_as_runtime.py with your favorite text editor. 
Go to line 115 where you will find the: blend_path += '.blend'
Remove it from there and add it under line 108 which says: tempdir = ...

ii) open your blender file which you want to save as a standalone file  and choose: 
File->user preferences...->Addons->Game engine-> and click the option Game Engine: Save as Game Engine Runtime

iii) Then go to File->export->Save as game engine runtime (mind that this option is not available if you do not do part ii)
and click the button Save as game engine runtime
Have in mind that in order to create your standalone file at the place where is says "cancel", at the left hand side, you will have to type a name. That name will be the one for your standalone file. It will be created along with a folder which will have the name of your blender version (for this one 2.69).

**9) How I will run my game?**

Navigate to the folder that you have saved your standalone file and type ./name_of_standalone_application

**10) While doing so I get the following errors:**
Color management: using fallback mode for management
connect failed: No such file or directory

**What do I do?**

I did not do anything. They did not affect in any way my project.

[B]11) While doing so I get another message: found bundled python
What about it?[/B]

It is normal. You do not have to worry.

[B]12) I have created the menu in one blend file. This menu has 4 subcategories. These correspond to 4 different blend files. How can I connect all these under one standalone application?
[/B]
Using the logic editor, and connecting all these files via game actuators from file, it won't end up with the result you want. For example, let us suppose that we want to create a menu with the following options:

i) play
ii) video
iii) help
iv) exit

The first one corresponds to your game and it occupies a different blend file from that of your menu.
The second one has mainly text and pictures.
The third one has mainly text as well.
The fourth one exits your game.

If each one of the above is a separate blend file, then from the logic editor you will be able to link them via game actuators. If now, you are willing to create a standalone application, it won't work. In other words, you won't be able to access the content of each of the options from your menu. Your menu will be ok, yet every time you click on an option, your program will exit.

In order to be able to make it work you will have to transfer each of the options (different blend files) as different **scenes** to your (original) blend file that you have created your menu.

So, you go to File->Append.

Now if you do that a new window will open from which you will be able to navigate to the blend file you are wishing to add as a new scene. Select it and at the moment you do so, you will be able to see that all the folders that comprise this blend file will be availabe. Choose the folder Scene and from there the file scene.

If you did the process correctly, on the top line of your blender (original menu) file where it says scene, if your press the arrows on the left, you will be able to see that a new scene has been created. If no previous scene existed, then the name of the new scene will be like: Scene.001
This one will have to be added in your actuator (the actuator will be of type: scene).
You will have to repeat that process for all the options you have created that way.

[B]13) I'm happy with the menu options, yet, every time I select an option I cannot go back to the menu. What can I do?

You will have to create a separate sensor in each of the different scenes which will do that for you.[/B]

So, we go to our first option which is our game. We select that scene and we choose the logic editor of that scene. As a (new) sensor we choose:keyboard
As a controller: the And controller
As an actuator: a scene actuator, and from there we will choose as scene our menu scene (in which we want to return to).

Every time we press the button we have assigned to that new sensor, we will return back to our menu.

**14) I have added animation to my game, yet it does not work. I have used the timeline.**

It won't work that way. You will have to add it via logic editor using the action actuator in order for your animation to work.

**15) I want to make one item appear and disappear. What can I do?**

Some people suggest to use layers and transfer your objects from layer to layer using timeline. It seems that it does not work in this version of blender. 
There were also other suggestions like choosing the object in question from the top right menu and clicking accordingly the restrict viewpoint visibility (eye) and restrict rendering (camera) buttons. It did not work for me in the standalone application, just only when pressing p in order to see a preview of their effect.
I suggest you to choose animation in such a way so as to transfer your object outside the camera's view and bring it back again.

**16) I'm adding animation pressing the i button, but for some reason my animation refuses to show up. Why?**

I faced this problem when I wanted to transfer my object away from screen. I had used timeline from frame 80 and on and I wanted my object to disappear from frames 1 till 80. So I took my object away from camera for frame 1, and I added it on sight at frame 79. Because 79 and 80 weren't connected my animation did not work. I had to use continuous animation in order for it to work.

**17) How do I select multiple items?**

Right click on them by pressing at the same time shift.

**18) How do I do undo?**

ctrl+z

If pressed multiple times, you go back more than one steps.

**19) I did not save my project and I closed it. What can I do?** 

Most probably you will find it under /tmp folder,
yet it is a nice idea to save your work because there is not an auto save button.

**20) I want to change the size of one of my objects and modify it, yet I have many objects on screen. What do I do?**

Initially go to object mode and with right click choose the object you want to modify.
Now choose the edit mode and modify you object. Every time you press a in order to select every vertice of the mesh of your object, only the vertices of the object in question will be chosen.

I hope that this clarifies some steps for future reference.

Regards!

---

