import junit.framework.TestCase;

public class RationalTest extends TestCase {

    protected Rational HALF;

    protected void setUp() {
      HALF = new Rational( 1, 2 );
    }

    // Create new test
    public RationalTest (String name) {
        super(name);
    }

    public void testEquality() {
        assertEquals(new Rational(1,3), new Rational(1,3));
        assertEquals(new Rational(1,3), new Rational(4,12));
        assertEquals(new Rational(3,3), new Rational(1,1));
        assertEquals(new Rational(0,99), new Rational(0,999));
        assertEquals(new Rational(0,-99), new Rational(-0,999));
        assertEquals(new Rational(-1,-99), new Rational(-10,-990));
        assertEquals(new Rational(-1,-99), new Rational(1,99));
        assertEquals(new Rational(1,-99), new Rational(-1,99));
        assertEquals(new Rational(-8,-4), new Rational(2,1));
        assertEquals(new Rational(16,-2), new Rational(-8,1));
        assertEquals(new Rational(222,-222), new Rational(-1111,1111));
        assertEquals(new Rational(-10000,-4), new Rational(2500,1));
        assertEquals(new Rational(0,-2), new Rational(0,1));
        assertEquals(new Rational(0000,-2), new Rational(000,1));
        assertEquals(new Rational(0000,2000), new Rational(000,-1));
    }

    public void testEqualityOnBoundary() {
        assertEquals(new Rational(4999,1000), new Rational(4999,1000));
    }

    // Test for nonequality
    public void testNonEquality() {
        assertFalse(new Rational(2,3).equals(
            new Rational(1,3)));
    }

    public void testAccessors() {
    	assertEquals(new Rational(2,3).numerator(), 2);
    	assertEquals(new Rational(2,3).denominator(), 3);
    	assertEquals(new Rational(-2,3).numerator(), -2);
    	assertEquals(new Rational(-2,-3).denominator(), 3);
    	assertEquals(new Rational(-2,-3).numerator(), 2);
    	assertEquals(new Rational(6,3).denominator(), 1);
    	assertEquals(new Rational(1000,1000).numerator(), 1);
    	assertEquals(new Rational(0,3).denominator(), 1);
    	assertEquals(new Rational(-0,-3).denominator(), 1);
    }
    
    public void testAccessorsWithDivision() {
    	assertEquals((new Rational(2,3).numerator())/(new Rational(2,3).denominator()), 1);
    	assertEquals((new Rational(-2,3).numerator())/(new Rational(2,-3).denominator()), 1);
    	assertEquals((new Rational(-2,3).numerator())/(new Rational(2,3).denominator()), -1);
    }

    public void testRoot() {
        Rational s = new Rational( 1, 4 );
        Rational sRoot = null;
        try {
            sRoot = s.root();
        } catch (IllegalArgumentToSquareRootException e) {
            e.printStackTrace();
        }
        assertTrue( sRoot.isLessThan( HALF.plus( Rational.getTolerance() ) ) 
                        && HALF.minus( Rational.getTolerance() ).isLessThan( sRoot ) );
    }

    public void testPlusSimple() {
        Rational a = new Rational( 1, 4);
        Rational b = new Rational(1,4); 
        Rational c = null;
        try {
            c = a.plus(b);
        } catch (Exception e) {
            e.printStackTrace();
        }
        Rational d = new Rational(1,2);
        assertTrue( c.equals(d));
    }

    public void testPlusBoundary() {
        Rational a = new Rational( 4999, 1000 );
        Rational b = new Rational(4999,1000); 
        Rational c = null;
        try {
            c = a.plus(b);
        } catch (Exception e) {
            e.printStackTrace();
        }
        Rational d = new Rational(9988,1000);
        assertTrue( c.equals(d));
    }

    public void testTimes() {
        assertEquals(new Rational(2,5).times(new Rational(3,6)), new Rational(1,5));
        assertEquals(new Rational(-1,5).times(new Rational(2,5)), new Rational(-2,25));
        assertEquals(new Rational(1000,999).times(new Rational(999,1000)), new Rational(1,1));
        assertEquals(new Rational(000,999).times(new Rational(000,1000)), new Rational(0,1));
        assertEquals(new Rational(0,-999).times(new Rational(-0,1000)), new Rational(0,1));
        assertEquals(new Rational(9,10).times(new Rational(-9,10)), new Rational(-81,100));
        assertEquals(new Rational(99,10).times(new Rational(99,10)), new Rational(9801,100));
        assertEquals(new Rational(999,100).times(new Rational(999,100)), new Rational(998001,10000));
        assertEquals(new Rational(-99,10).times(new Rational(99,10)), new Rational(9801,-100));
        assertEquals(new Rational(-99,10).times(new Rational(99,-10)), new Rational(9801,100));
        assertEquals(new Rational(-99,-10).times(new Rational(-99,10)), new Rational(9801,-100));
}

    public void testMinus() {
        assertEquals(new Rational(9999,1000).minus(new Rational(9999,1000)), new Rational(0,100));
        assertEquals(new Rational(0,-1000).minus(new Rational(-9999,-1000)), new Rational(-9999,1000));
        assertEquals(new Rational(9999,1000).minus(new Rational(9999,-1000)), new Rational(19998,1000));
        assertEquals(new Rational(-0,-1000).minus(new Rational(-9999,-1000)), new Rational(9999,-1000));
        assertEquals(new Rational(-1111,-1000).minus(new Rational(-1111,-1000)), new Rational(0,1));
        assertEquals(new Rational(5,3).minus(new Rational(4,3)), new Rational(1,3));
        assertEquals(new Rational(-0,-1000).minus(new Rational(-0,-1000)), new Rational(0,-1000));
    }

    public void testTimesWithMinus() {
        assertEquals((new Rational(2,5).times(new Rational(3,6))).minus(new Rational(2,5).times(new Rational(3,6))), new Rational(0,-1000));
        assertEquals((new Rational(99,10).times(new Rational(99,10))).minus(new Rational(99,10).times(new Rational(99,10))), new Rational(0,1));
    }

    public void testDivides() {
        Rational a = new Rational(999,1000);
        Rational b = new Rational(1000,999);

        assertEquals(b.divides(a), new Rational(1,1));
    }

    public void testDividesZeroCase() {
        Rational a = new Rational(0,1000);
        Rational b = new Rational(1,999);

        assertEquals(b.divides(a), new Rational(0,1));
    }

    public void testIsLessThan() {
        assertTrue(new Rational(1,5).isLessThan(new Rational(1,2)));
        assertTrue(new Rational(-1,2).isLessThan(new Rational(1,5)));
        assertTrue(new Rational(-1,6).isLessThan(new Rational(0,5)));
        assertTrue(new Rational(-1,6).isLessThan(new Rational(6,3)));
        assertTrue(new Rational(-6,3).isLessThan(new Rational(-0,-3)));
}

    public void testAbs() {
        Rational a = new Rational(-4999,1000);
        Rational b = new Rational(5,-5);
        Rational c = new Rational(-0,-2);
        Rational d = new Rational(3,3);

        assertEquals(a.abs(), new Rational(4999,1000));
        assertEquals(b.abs(), new Rational(1,1));
        assertEquals(c.abs(), new Rational(0,777));
        assertEquals(d.abs(), new Rational(7,7));
    }

    public void testToString() {
        assertEquals(new Rational(1,1).toString(), "1/1");
        assertEquals(new Rational(6,2).toString(), "3/1");
        assertEquals(new Rational(-6,2).toString(), "-3/1");
        assertEquals(new Rational(-6,-2).toString(), "3/1");
    }

    public void testToStringZeroCases() {
        assertEquals(new Rational(-0,2).toString(), "0/1");
        assertEquals(new Rational(0,-2).toString(), "0/1");
        assertEquals(new Rational(-1000,2).toString(), "-500/1");
    }
    
    public void testSetTolerance() {
        Rational a = new Rational(1,1500);
        Rational b = new Rational(Rational.getTolerance().numerator(), Rational.getTolerance().denominator());

        Rational.setTolerance(a);
        assertEquals(Rational.getTolerance(),a);

        Rational.setTolerance(b);
        assertEquals(Rational.getTolerance(),b);
    }
  
    public void testNumerator() {
        assertEquals(new Rational(4999,1000).numerator(), 4999);
        assertEquals(new Rational(0,4).numerator(), 0);
        assertEquals(new Rational(2345,-456788).numerator(), 2345);
        assertEquals(new Rational(8,4).numerator(), 2);
        assertEquals(new Rational(0,-4).numerator(), 0);
        assertEquals(new Rational(-0,4).numerator(), 0);
        assertEquals(new Rational(-10067,-4).numerator(), 10067);
}

	public void testDenominator() {
	        assertEquals(new Rational(1,345).denominator(), 345);
	        assertEquals(new Rational(0, 4).denominator(), 1);
	        assertEquals(new Rational(8, 4).denominator(), 1);
	        assertEquals(new Rational(0,-4).denominator(), 1);
	}
	
	public void testOverflowViaLCM(){
		Rational a = new Rational(1,2147483647);
		Rational b = new Rational(1,2);
		assertEquals(a.plus(b).denominator()/2, 2147483647);
	}
	
	public void testMain(){
		Rational a = new Rational(1,2);
		a.main(null);
	}
	
    public static void main(String args[]) {
        String[] testCaseName = 
            { RationalTest.class.getName() };
        // junit.swingui.TestRunner.main(testCaseName);
        junit.textui.TestRunner.main(testCaseName);
    }
}
