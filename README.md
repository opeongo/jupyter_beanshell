# Jupyter Beanshell kernel

This project implememts a BeanShell kernel for Jupyter Notebokks based on the [Juptyer JVM BaseKernel project by Spencer Park](https://github.com/SpencerPark/jupyter-jvm-basekernel).  The project is a simple wrapper to start a Beanshell interpreter using the JSR223 script engine factory, and then call eval() to do all of the work.

### Compiling

1. Adjust dependency versions and repository locations as required.

2. Compile with gradlew:
```
gradlew clean jar
```

### Installing
1. Copy the resulting `beanshell_kernel-1.0.0.jar` file to a reliable location, for example to /home/me/jupyter_beanshell.

2. Create a kernel.json specification file similar to the following:
```
{
 "argv": ["java",
          "-classpath",
              "/home/me/jupyter_beanshell/beanshell_kernel-1.0.0.jar",
              "ca.spatial.jupyter.IBeanshell",
              "{connection_file}"],
 "display_name": "BeanShell",
 "language": "beanshell"
}
````
For example, create this file as /home/me/jupyter_beanshell/kernel.json


3. Install the kernel in the usual way by specifying the name of the folder that contains the kernel.json file:

```
jupyter kernelspec install /home/me/jupyter_beanshell
```

4. Start the notebook application, and select the "BeanShell" kernel.
