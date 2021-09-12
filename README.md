# curly-robot
Write a program to demonstrate friend class behaviour. Friend class functions will access the data members of the other class.  

#include <iostream> 
#include<string.h> 
using namespace std; 
class Sales; 
class Employees 
{ 
    char name[100], dept[100]; 
    int id, salary; 
 
public: 
    void getDetails() 
    { 
        cout << "Enter name:"; 
        cin >> name; 
        cout << "Enter department:"; 
        cin >> dept; 
        cout << "Enter id:"; 
        cin >> id; 
        cout << "Enter salary:"; 
        cin >> salary; 
    } 
    void showDetails() 
    { 
        cout << "Name:" << name << endl; 
        cout << "Department:" << dept << endl; 
        cout << "Id:" << id << endl; 
        cout << "Salary:" << salary << endl; 
    } 
    friend class Sales; 
}; 
 
class Sales 
{ 
    int sales, incentives; 
    char performance[10]; 

public: 
    void getData() 
    { 
        cout << "Enter sales:"; 
        cin >> sales; 
    } 
    void printData(Employees emp, int units) 
    { 
        if (units > 50 && units < 100) 
        { 
            incentives = emp.salary / 10; 
        } 
        else if (units > 100 && units < 150) 
        { 
            incentives = emp.salary / 5; 
        } 
        else if (units > 150) 
        { 
            incentives = (3 / 10) * emp.salary; 
        } 
        if (sales < 50) 
        { 
            strcpy(performance, "Poor"); 
        } 
        else if (sales < 100) 
        { 
            strcpy(performance, "Satisfactory"); 
        } 
        else if (sales < 150) 
        { 
            strcpy(performance, "Good"); 
        } 
        else 
        { 
            strcpy(performance, "Excellent"); 
        } 
        cout << "Sales:" << sales << endl; 
        cout << "Incentives acquired:" << incentives << endl; 
        cout << "Performance:" << performance; 
    } 
}; 
int main() 
{ 
    Employees emp; 
    Sales s; 
    emp.getDetails(); 
    emp.showDetails(); 
    s.getData(); 
    s.printData(emp, 80); 
    return 0; 
}
