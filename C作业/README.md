# practice1
package test;

public class Test{
public static void main(String args[]) throws CloneNotSupportedException{
Octagon o1=new Octagon(5);
System.out.println("the Object1's Area is "+o1.getArea());
System.out.println("the Object1's Perimeter is "+o1.getPerimeter());
Octagon o2=(Octagon)o1.clone();
int result=o1.compareTo(o2);
if(result>0){
System.out.println("the object1 > object2");
}
else if(result<0){
System.out.println("the object1 < object2");
}
else
    System.out.println("the object1 = object2");
}
}

class Octagon extends GemometricObject implements Cloneable,Comparable<Octagon>{
private int radius=1;
Octagon(){};
Octagon (int radius){
this.radius=radius;
}
@Override
public double getArea() {
return (2+4/(Math.sqrt(2)))*radius*radius;
}
@Override
public double getPerimeter() {
return 8*radius;
}
@Override
public int compareTo(Octagon a) {
if(getArea()>a.getArea()){
return 1;        
}
else if(getArea()<a.getArea()){
return -1;
}
else
    return 0;
}
public Object clone() throws CloneNotSupportedException{
return super.clone();
}
}


abstract class GemometricObject{
private String color="white";
private boolean filled;
private java.util.Date dateCreated;
protected GemometricObject(){
dateCreated =new java.util.Date();
}
protected GemometricObject(String color,boolean filled){
this.color=color;
this.filled=filled;
}
public String getColor(){
return color;
}
public boolean isFilled(){
return filled;
}
public void setFilled(boolean filled){
this.filled=filled;
}
public java.util.Date getDateCreated(){
return dateCreated;
}
@Override
public String toString(){
return "created on"+dateCreated+"\ncolor: "+color+" and filled: "+filled;
}
public abstract double getArea();
public abstract double getPerimeter();
}
