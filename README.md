# QEMU on Universal Windows Platform
A project to build qemu on Xbox One and more

This isn't garunteed to be updated, it's just one of my many useless tinkering projects.

# Problems
QEMU is a large C project, so this primarily involves porting a makefile project to a VS2017 solution or something that can build a UWP APPX.
</br>I don't know how QEMU's build process works and I'm not experienced with makefile, however there is a possible work around.

# Ideas on how this could work:
## Wrapping QEMU as a native library into a UWP Library
This could be done by using VS2017's makefile tools to build QEMU as a library. Then take said library and wrap it in a UWP compatible library.

## Simply converting the makefile to a VS2017 solution
I found a project <a href="https://github.com/xHypervisor/WinQEMU">here</a> that has already done this with much earlier versions of QEMU. However the solution is a bit old and converting it to VS2017 didn't work properly for me. This is probably the best way to make it work, I just need to learn more about upgrading solutions or else learn to translate a makefile project to a VS solution.

## Using <a href="https://github.com/bdbai/firstuwp-rs">rust</a> via <a href="https://github.com/jameysharp/corrode">corrode</a>
I think it will be much easier to combine UWP and QEMU under rust instead of VS using the firstuwp-rs project as a template and corrode to convert the makefile project to a rust project.

## Intergrating <a href="https://github.com/bdbai/firstuwp-rs">UWP</a> via a <a href="https://github.com/AndrewGaspar/corrosion">rust crate</a> from a cmake version of QEMU
So like the title implies, this path requires converting QEMU's makefile to a cmake project. Corrosion is much younger and more hip than Corrode and therefore should probably work better with QEMU's newer source but I just don't have a cmake project for QEMU yet.

# Graphics
## Notes on OpenGL and SDL in UWP
As you probably know, the Xbox One along with UWP in general only supports Direct X as opposed to OpenGL. I've even tried using <a href="https://github.com/j4m3z0r/GLUWP">this ANGLE method</a>, and while it built properly on my PC, it somehow did not deliver on Xbox One. All that aside, QEMU uses SDL and not OpenGL directly as far as I know. So maybe it can be build with SDL targeting Direct X (WinRT platform)? Again I'm not too keen on how to do that yet as I haven't done alot with SDL in my life.

## KVM?
atm I doubt KVM is possible so I'm not prioritizing it. I'm not completely educated on what kind of access the Xbox One provides and what KVM exactly needs. However I wanna research this more in case it is possible.
