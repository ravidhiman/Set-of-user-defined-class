#include<iostream>
#include<set>
using namespace std;

class Product
{
	int price;
	int id;
	string desc;
public:
	Product(int id, int price, string desc) :id(id), price(price), desc(desc) {}
	int getId() const
	{
		return id;
	}
	int getPrice() const
	{
		return price;
	}
	string getDesc() const
	{
		return desc;
	}

	//less than Operator overloading
	bool operator < (const Product & P) const
	{
		return id < P.id;
	}
};

ostream& operator<<(ostream& out,const Product &P)
{
	out << P.getId() << " " << P.getPrice() << " " << P.getDesc().c_str() << endl;
	return out;
}

//functor
struct comp
{
	bool operator()(const Product& P1, const Product& P2)
	{
		return P1.getId() < P2.getId();
	}
};

//function
bool compare(const Product& P1, const Product& P2)
{
	return P1.getId() < P2.getId();
}

int main()
{
	
	//1. using compare function
	//set<Product, bool(*)(const Product&, const Product&)> mySet(compare);
	
	//2. using functor 
	//set<Product, comp> mySet;

	//3. using < operator
	//set<Product> mySet;

	//4. using lambda
	auto lam = [](const Product& P1, const Product& P2)->bool {return P1.getId() < P2.getId();};
	set<Product, decltype(lam)> mySet(lam);

	mySet.insert(Product(2, 40, "xyz"));
	mySet.insert(Product(1, 30, "abc"));
	for (auto i = mySet.begin();i != mySet.end();i++)
	{
		cout << *i << endl;
	}
	return 0;
};
